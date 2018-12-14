<template>
    <div class="container">
        <view class="logo_box">
            <view class="logo">
                <image src="/static/images/logo_img.png"></image>
            </view>
            <view class="logo_titile">共享充电宝租赁</view>
            <image class="second" src="/static/images/second.png"></image>
        </view>
        <view class="footer_box">
            <view class="footer-top">
                <view class="tips">用户协议</view>
                <view class="xian"></view>
                <view class="tips">隐私声明</view>
            </view>
            <view class="copy">Copyright 深圳市摩登兄弟科技有限公司保留所有权利</view>
        </view>
    </div>
</template>
<script>
    export default {
        data() {
            return {}
        }
    }
</script>
<style lang="less" scoped>
page {
    width: 100%;
    height: 100%;
    position: relative;
}
.container {
    
    .logo_box {
        width: 400rpx;
        height: 400rpx;
        position: absolute;
        /* background-color: pink; */
        top: 160rpx;
        left: 50%;
        transform: translateX(-50%);
        .logo {
            width: 180rpx;
            height: 180rpx;
            background-color: #201e2c;
            border-radius: 30rpx;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto;
            image {
                width: 102rpx;
                height: 83rpx;
            }
        }
        .logo_titile {
            font-size: 30rpx;
            font-family: PingFang-SC-Light;
            font-weight: 300;
            color: #201e2c;
            text-align: center;
            padding-top: 36rpx;
        }
        .second {
            width: 106rpx;
            height: 23rpx;
            float: right;
            margin-right: 40rpx;
        }
    }
    .footer_box {
        width: 100%;
        position: absolute;
        bottom: 60rpx;
        left: 50%;
        transform: translateX(-50%);
        .footer-top {
            display: flex;
            align-items: center;
            justify-content: center;
            height: 24rpx;
            .tips {
                font-size: 24rpx;
                color: #999;
            }
            .xian {
                width: 1px;
                height: 100%;
                background-color: #999999;
                margin: 0px 10rpx;
            }
        }
        .copy {
            font-size: 24rpx;
            color: #999;
            text-align: center;
            padding-top: 20rpx;
        }
    }
}
    
</style>


