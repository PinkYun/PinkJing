<template>
    <div class="container">
        <view class="title">¥ <text>{{price}}.00</text>元/1小时</view>
        <view class="number">需缴纳押金<text>99</text>元</view>
        <image class="jiao_img" src="/static/images/jiaona_img.png"></image>
        <button :disabled="disabled" class="button" :class="isTrue?'active':''" @tap="getyajin">立即租借</button>
        <view class="tip">押金在充电宝归还后即可退回,<text class="toindex" @tap="toIndex">返回首页</text></view>
    </div>
</template>
<script>
import bus from '../../bus/bus.js'
import { setTimeout } from 'timers';
    export default {
        data() {
            return {
                price: 2,
                disabled: false,
                isTrue: false,
            }
        },
        methods: {
            // 返回首页
            toIndex(){
                wx.redirectTo({url: '/pages/index/main'})
            },
            getyajin(){
                this.isTrue = true
                this.disabled = true
                wx.showLoading({
                    title: '正在租借',
                    mask: true,
                });
                setTimeout(()=>{
                    this.isTrue = false
                    this.disabled = false
                    wx.reLaunch({url: '/pages/success/main'})
                    wx.hideLoading();
                },2000)
            }
        },
        created(){
            
        }
    }
</script>
<style lang="less" scoped>
.container {
    padding-top: 120rpx;
    padding-left: 30rpx;
    padding-right: 30rpx;
    .title {
        font-size: 34rpx;
        color: #333;
        text-align: center;
        margin-bottom: 38rpx;
        text {
            font-size: 72rpx;
            font-family: PingFang-SC-Medium;
        }
    }
    .number {
        text-align: center;
        font-size: 36rpx;
        color: #202020;
        text {
            color: #FD5153;
        }
    }
    .jiao_img {
        display: block;
        margin: 50rpx auto 60rpx;
        width: 305rpx;
        height: 405rpx;
    }
    button::after {
        border: none!important;
        padding: 0;
    }
    .button {
        width: 100%;
        height: 88rpx;
        line-height: 88rpx;
        text-align: center;
        border-radius: 44rpx;
        background-color: #F7D123;
        color: #333;
        font-size: 36rpx;
    }
    .active {
        background-color: #fff;
        border: 1px solid #ccc;
    }
    .tip {
        font-size: 24rpx;
        color: #333;
        height: 30rpx;
        margin-top: 30rpx;
        text-align: center;
        .toindex {
            color: #F7D123;
            font-size: 28rpx;
            margin-left: 10rpx; // border-bottom: 1px solid #F7D123;
        }
    }
}
</style>


