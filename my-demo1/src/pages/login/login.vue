<template>
    <view class="page">
        <view class="header">
            <image class="logo" src="/static/images/logo_top.png"></image>
        </view>
        <view class="content">
          <text class="text">为了保证正常的运营,需要您授权您的基本信息</text>
          <text class="text"> 
            (基本信息仅包含邮箱,昵称等数据),您的信息</text>
          <text class="text">将
            按照用户协议严格保密,请点击"允许"按钮授权。</text>
        </view>
        <button class="share-btn" open-type="getUserInfo" @getuserinfo="setting">允 许</button>
    </view>
</template>

<script>
export default {
    data(){
        return {
            isTrue: false,
            userinfo: '',
        }
    },
    methods: {
        setting(){
            wx.login({
                success: (res)=>{
                //    console.log(res)
                   wx.getUserInfo({
                       withCredentials: 'true',
                       lang: 'zh_CN',
                       success: (res)=>{
                        // console.log(res)
                        if(res.userInfo){
                            wx.setStorageSync('userinfo', res.userInfo);
                            wx.reLaunch({
                                url: '/pages/index/main'
                            })
                        }
                       },   
                       fail: ()=>{},
                       complete: ()=>{}
                   });     
                },
                fail: ()=>{},
                complete: ()=>{}
            });
        }
    },
    cearted(){

    }
}
</script>
<style lang="less">
.page {
  background-color: #fff;
  box-sizing: border-box;
  padding: 0px 30rpx;
  .logo {
    width: 275rpx;
    height: 223rpx;
    text-align: center;
    margin: 120rpx auto 0px;
    display: block;
  }
  .content {
    padding: 80rpx 10rpx 120rpx;
    // width: calc(100vw-120rpx);
    width: 100%;
    box-sizing: border-box;
    text-align: center;
    // padding-left: 20rpx;
    .text {
      width: 100%;
      font-size: 30rpx;
      color: #666;
      line-height: 30rpx;
      // text-align: center;
      // box-sizing: border-box;
      // margin-left: 30rpx;
    }
  }
  button::after {
    border: 0px;
  }
  button {
    border: 0px; 
  }
  .share-btn {
    width: 100%;
    height: 88rpx;
    line-height: 88rpx;
    text-align: center;
    background-color: #f7d123;
    color: #333;
    font-size: 36rpx;
    border-radius: 44rpx;
  }
  .active {
      background-color: #fff;
      border: 1px solid #aaa;
  }

}
</style>