<template>
    <div class="container">
        <view class="bd">账号绑定</view>
        <view class="account_box">
            <view class="account_list" @tap="editwechat">
                <view class="wechat_img">
                    <image src="/static/images/bind/wechart.png"></image>
                    <view class="wechat">微信</view>
                </view>
                <view class="wechat_r">
                    <view class="r_name">{{userinfo.nickName}}</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
            <view class="account_list phone_box" @tap="editmobile">
                <view class="wechat_img">
                    <image src="/static/images/bind/phone.png"></image>
                    <view class="wechat">手机</view>
                </view>
                <view class="wechat_r">
                    <view class="r_name">未绑定</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
        </view>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                userinfo: '',
            }
        },
        methods: {
            editwechat(){
                wx.showToast({
                    title: '暂不支持修改',
                    icon: 'none',
                    duration: 1500,
                    mask: false,
                });
            },
            editmobile(){
                wx.showToast({
                    title: '暂未开放..',
                    icon: 'none',
                    duration: 1500,
                    mask: false,
                });
            }
        },
        created(){
            this.userinfo = wx.getStorageSync('userinfo');
            // console.log(this.userinfo)
        }
    }
</script>
<style lang="less" scoped>
.container {
    width: 100%;
    height: 100%;
    background-color: #efeff4;
}
.bd {
  height: 80rpx;
  width: 100%;
  font-size: 28rpx;
  font-family: PingFang-SC-Medium;
  font-weight: 500;
  line-height: 80rpx;
  margin-left: 30rpx;
}
.account_box {
  background-color: #fff;
  width: 100%;
  box-sizing: border-box;
  padding: 0px 30rpx;
  .account_list {
    width: 100%;
    height: 120rpx;
    display: flex;
    align-items: center;
    justify-content: space-between;
    border-bottom: 1px solid #e5e5e5;
    .wechat_img {
      display: flex;
      align-items: center;
      image {
        width: 60rpx;
        height: 60rpx;
      }
      .wechat {
        font-size: 30rpx;
        font-family: PingFang-SC-Medium;
        font-weight: 500;
        color: #000;
        margin-left: 20rpx;
      }
    }
    .wechat_r {
      display: flex;
      align-items: center;
      .r_name {
        font-size: 28rpx;
        color: #999;
      }
      .jiantou {
        width: 12rpx;
        height: 24rpx;
        margin-left: 20rpx;
      }
    }
  }
  .phone_box {
      border-bottom: 0px;
    }
}
</style>


