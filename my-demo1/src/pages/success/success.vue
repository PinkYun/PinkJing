<template>
    <div class="container">
        <view class="img_success">
            <image src="/static/images/success.png"></image>
        </view>
        <view class="title">租借成功</view>
        <view class="tip1">请取弹出的充电宝。</view>
        <view class="tip1">若充电宝未正常弹出，请拨打客服电话联系我们~</view>
        <!-- <view class="button" @tap="toOrderList">查看订单</view> -->
        <view class="button1" @tap="toIndex">返回首页</view>
        <view class="tip_box">
            <view class="tip2">
                <text class="tip">温馨提示</text>
                <text>每24小时租金封顶20元,当押金为0时</text>
                <text>充电宝归个人所有,无法归还</text>
            </view>
        </view>
    </div>
</template>
<script>
    export default {
        data() {
            return {}
        },
        methods:{
            toIndex(){
                wx.redirectTo({url: '/pages/index/main'})
            }
        }
    }
</script>
<style lang="less" scoped>
.container {
    width: 100%;
    box-sizing: border-box;
    padding: 100rpx 30rpx 0px;
    .img_success {
        margin: 0 auto;
        width: 200rpx;
        height: 200rpx;
        margin-bottom: 58rpx;
        image {
            width: 100%;
            height: 100%;
        }
    }
    .title {
        text-align: center;
        font-size: 40rpx;
        font-family: PingFang-SC-Medium;
        font-weight: 500;
        color: #000;
        margin-bottom: 58rpx;
    }
    .tip1 {
        text-align: center;
        color: #666;
        font-size: 24rpx;
        margin-bottom: 20rpx;
    }
    .button,
    .button1 {
        width: 100%;
        height: 88rpx;
        line-height: 88rpx;
        text-align: center;
        background-color: #F7D123;
        font-size: 36rpx;
        color: #333;
        border-radius: 44rpx;
        margin-top: 100rpx;
    }
    .button1 {
        margin-top: 30rpx;
        border:1px solid rgba(214,213,214,1);
        background-color: #FBFAFC;
    }
    .tip_box {
        width: 100%;
        position: fixed;
        bottom: 80rpx;
        left: 50%;
        transform: translateX(-50%);
        .tip2 {
            padding-top: 140rpx;
            font-size: 28rpx;
            display: flex;
            flex-direction: column;
            color: #666;
            align-items: center;
            justify-content: center;
            .tip {
                color: #F7D123;
            }
        }
    }
    
}
</style>


