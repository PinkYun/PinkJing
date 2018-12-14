<template>
    <div class="container">
        <view class="mask" v-if="isTrue"></view>
        <view class="phone_box" v-if="isTrue">
            <view class="phone_title">客服电话</view>
            <view class="phone_tips">是否拨打 0755-83257443</view>
            <view class="xian"></view>
            <view class="sure_box">
                <view class="button" @tap="quxiao">取消</view>
                <view class="r_xian"></view>
                <view class="button sure" @tap="getPhone">确定</view>
            </view>
        </view>
    </div>
</template>
<script>
    export default {
        data(){
            return {
                isTrue: false
            }
        },
        methods: {
            // 拨打电话
            bindcall() {
                this.isTrue = true
            },
            quxiao() {
                this.isTrue = false
            },
            getPhone() {
                wx.makePhoneCall({
                    phoneNumber: '0755-83257443'
                })
            },
        }
    }
</script>
<style lang="less" scoped>
 .mask {
    width: 100%;
    height: 100%;
    position: absolute;
    z-index: 111;
    left: 0px;
    top: 0px;
    background-color: #000;
    opacity: 0.5;
  }
  .phone_box {
    width: 560rpx;
    height: 290rpx;
    position: absolute;
    z-index: 112;
    background-color: #fff;
    border-radius: 10rpx;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    box-sizing: border-box;
    padding-top: 20rpx;
    box-sizing: border-box;
    .phone_title {
      width: 100%;
      text-align: center;
      height: 100rpx;
      line-height: 100rpx;
      font-size: 36rpx;
      color: #333;
      font-family: PingFang-SC-Medium;
    }
    .phone_tips {
      font-size: 28rpx;
      color: #666;
      text-align: center;
      height: 70rpx;
    }
    .xian {
      width: 100%;
      height: 1px;
      background-color: #d2d3d5;
    }
    .sure_box {
      width: 100%;
      height: 100rpx;
      display: flex;
      align-items: center;
      /* border-top: 1rpx solid #D2D3D5; */
      .button {
        flex: 1;
        height: 100%;
        text-align: center;
        line-height: 100rpx;
        font-size: 34rpx;
      }
      .r_xian {
        width: 1px;
        height: 100%;
        background-color: #d2d3d5;
      }
      .sure {
        color: #F7D123;
      }
    }
  }
</style>


