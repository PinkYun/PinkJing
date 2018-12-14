<template>
    <div class="container">
        <view class="user_box">
            <image src="/static/images/user_bg.png"></image>
            <view class="top_box">
                <view class="title">押金</view>
                <view class="price">¥ <text>{{price}}.00</text></view>
            </view>
        </view>
        <view class="button_box">
            <view class="button" @tap="getRefund">退款</view>
        </view>
        <view class="tips">
            <view class="title">温馨提示:</view>
            <view class="title title1">充电宝归还后押金将立即原路退还，到账时间为0-2小时，超过24小时未到账请联系客服处理。</view>
        </view>
        <view class="user_bottom">
            <view class="record_box" @tap="gotopage" data-page="/pages/record/main">
                <view class="img_l">
                    <image src="/static/images/zujie_img.png"></image>
                </view>
                <view class="img_r">
                    <view>租借记录</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
            <view class="record_box bangding" @tap="gotopage" data-page="/pages/bangding/main">
                <view class="img_l">
                    <image src="/static/images/bangding_img.png"></image>
                </view>
                <view class="img_r border_b">
                    <view>手机号绑定</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
        </view>
        <view class="user_bottom">
            <view class="record_box">
                <view class="img_l">
                    <image src="/static/images/help_img.png"></image>
                </view>
                <view class="img_r" @tap="gotopage" data-page="/pages/helpCenter/main">
                    <view>帮助中心</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
            <view class="record_box bangding" bindtap="bindcall">
                <view class="img_l">
                    <image src="/static/images/kefu_img.png"></image>
                </view>
                <view class="img_r border_b" @tap="gettips">
                    <view>客服电话</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
        </view>
        <view class="user_bottom">
            <view class="record_box " @tap="gotopage" data-page="/pages/about/main">
                <view class="img_l">
                    <image src="/static/images/about_img.png"></image>
                </view>
                <view class="img_r border_b">
                    <view>关于柠檬小宝</view>
                    <image class="jiantou" src="/static/images/ic_next.png"></image>
                </view>
            </view>
        </view>
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
    import bus from '../../bus/bus.js'
    export default {
        data() {
            return {
                isTrue: false,
                price: 99,
            }
        },
        // compponents:{
        //     tips
        // },
        methods: {
            gotopage(event) {
                // console.log(event.currentTarget.dataset.page)
                let url = event.currentTarget.dataset.page
                wx.navigateTo({
                    url: url
                });
            },
            gettips() {
                this.isTrue = true
            },
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
            getRefund() {
                if (this.price == 0) {
                    wx.showToast({
                        title: '没钱咋退..亲',
                        icon: 'none',
                        duration: 1500,
                        mask: false,
                    });
                } else {
                    wx.showToast({
                        title: '系统出错了...',
                        icon: 'none',
                        duration: 1500,
                        mask: false,
                    });
                }
            }
        },
        created() {
            // 发送非父子组件之间的值 
            bus.$emit('price', this.price)
        }
    }
</script>
<style lang="less" scoped>
    page {
        width: 100%;
        height: 100%;
        background-color: #efeff4;
        position: relative;
    }
    .container {
        width: 100%;
        height: 100%;
        background-color: #efeff4;
        .user_box {
            width: 100%;
            height: 378rpx;
            background-color: #fff;
            box-sizing: border-box;
            position: relative;
            image {
                width: 100%;
                height: 100%;
            }
            .top_box {
                position: absolute;
                left: 50%;
                transform: translateX(-50%);
                top: 65rpx;
                .title {
                    font-size: 32rpx;
                    color: #333;
                    margin-bottom: 8rpx;
                    text-align: center;
                }
                .price {
                    font-size: 34rpx;
                    color: #000;
                    text {
                        font-size: 48rpx;
                        color: #000;
                        font-family: PingFang-SC-Medium;
                        font-weight: 500;
                    }
                }
            }
        }
        .tips {
            padding: 16rpx 30rpx;
            .title {
                color: #000;
                font-size: 30rpx;
            }
            .title1 {
                color: #666;
                font-size: 28rpx;
            }
        }
        .button_box {
            width: 100%;
            height: 166rpx;
            background-color: #fff;
            box-sizing: border-box;
            padding: 38rpx 30rpx;
            margin-bottom: 20rpx;
            .button {
                width: 100%;
                height: 88rpx;
                line-height: 88rpx;
                text-align: center;
                background-color: #F7D123;
                font-size: 36rpx;
                color: #333;
                border-radius: 44rpx;
            }
        }
        .user_bottom {
            width: 100%;
            box-sizing: border-box;
            padding: 0px 30rpx;
            background-color: #fff;
            .record_box {
                height: 100rpx;
                width: 100%;
                display: flex;
                align-items: center;
                justify-content: space-between;
                .img_l {
                    width: 40rpx;
                    height: 40rpx;
                    image {
                        width: 40rpx;
                        height: 40rpx;
                    }
                }
                .img_r {
                    display: flex;
                    align-items: center;
                    justify-content: space-between;
                    flex: 1;
                    border-bottom: 1px solid #e5e5e5;
                    height: 100%;
                    margin-left: 14rpx;
                    view {
                        font-size: 30rpx;
                        color: #333;
                        padding-left: 8rpx;
                    }
                    .jiantou {
                        width: 12rpx;
                        height: 24rpx;
                    }
                }
                .border_b {
                    border-bottom: 0px;
                }
            }
            .bangding {
                margin-bottom: 20rpx;
            }
        }
        .mask {
            width: 100%;
            height: 100%;
            position: fixed;
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
    }
</style>
