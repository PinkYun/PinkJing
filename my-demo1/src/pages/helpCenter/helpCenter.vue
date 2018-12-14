<template>
    <view class='container'>
        <view class="centent_box">
            <block v-for="(item,index) in arrdata" :key="index">
                <view class="centent_title" @tap="open_that(index)" >
                    <view class="title">{{item.name}}</view>
                    <image v-show="item.isTrue==false" src="/static/images/ic_down.png"></image>
                    <image v-show="item.isTrue==true" src="/static/images/ic_top111.png"></image>
                </view>
                <view class="content_detail" v-show="item.isTrue">
                    <text>{{item.content}}</text>
                </view>
            </block>
        </view>
        <view class="bottom" @tap="toPhone">
            <view class="bot_box">
                <image class="icon_kefu" src="/static/images/icon_kefu_b.png"></image>
                <view class="kefu">联系客服</view>
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
    </view>
</template>
<script>
    export default {
        data() {
            return {
                code: '',
                selectedIndex: 0,
                isTrue: false,
                arrdata: [{
                        id: 1,
                        name: '如何计费?',
                        content: '采用分时计费规则,从借出充电宝后开始计时,归还充电宝后结束,具体价格以租借时页面展示的计费规则为准,每天封顶20元,计时消费超出20元,按封顶价格计费',
                        isTrue: false
                    },
                    {
                        id: 2,
                        name: '归还充电宝未结束订单?',
                        content: '请进行再次扫码点击租借按钮,此刻会退还上一笔押金余额,如需再借请支付,押金退还时间0-2小时,如两小时后未到账请联系客服',
                        isTrue: false
                    },
                    {
                        id: 3,
                        name: '为什么充值了,机柜却没有弹出充电宝?',
                        content: '充值了没有弹出充电宝,可能充电机柜和充电宝在使用过程中的磨损,导致无法正常弹出充电宝,请放心,没有弹出充电宝是不计算费用的,请重新进行一次租借操作',
                        isTrue: false
                    },
                    {
                        id: 4,
                        name: '能否请朋友帮忙归还充电宝?',
                        content: '当您使用充电宝之后,借给他人使用时,只要您朋友使用完,可以找到附近商店的机柜插入成功即可,系统会结算充电费用,您将会收到退回押金余额的信息',
                        isTrue: false
                    },
                    {
                        id: 5,
                        name: '能否租借多个充电宝?',
                        content: '暂时不支持一人租借多个充电宝,只能租借一个,租借结束后可以再次租借',
                        isTrue: false
                    },
                    {
                        id: 6,
                        name: '押金规则?',
                        content: `押金充值
                        在每次使用前需要缴纳押金99元,在每次使用完归还后,会自动结束计费,并在押金中扣除充电费用
                        
                        押金退还
                        在用户归还充电宝到机柜之后,系统会结束订单,并扣除充电费用,剩下的押金余额会原路退回,退款时间为0-2小时之内`,
                        isTrue: false
                    },
                    {
                        id: 7,
                        name: '如何租借充电宝?',
                        content: '扫码成功进入租借页面之后,点击立即租借,支付完押金后,请记得点击完成,等待机柜响应便可弹出充电宝',
                        isTrue: false
                    },
                    {
                        id: 8,
                        name: '押金未退回?',
                        content: '若押金未退回,请查看押金是否存在?若押金存在,请扫码租借并在归还充电宝后,0-2小时内退还押金,该种情况可能是充值后未点击完成支付,若不能解决,请在租借订单页面提交异常',
                        isTrue: false
                    },
                    {
                        id: 9,
                        name: '机柜充电宝电量低,未能借出?',
                        content: '在小程序扫码进入租借界面,点击立即租借,可自动结束订单,并退还押金,押金退回时间为0-2小时内',
                        isTrue: false
                    },
                ]
            }
        },
        methods: {
            open_that(index) {
            //   console.log(index)
                this.selectedIndex = index;
                for(var i = 0 ; i < this.arrdata.length;i++){
                    if(this.selectedIndex!=i){
                    this.arrdata[i].isTrue =false;
                    }
                }
                this.arrdata[this.selectedIndex].isTrue = !this.arrdata[this.selectedIndex].isTrue;

            },
            // 拨打电话
            toPhone() {
                this.isTrue = true;
            },
            quxiao() {
                this.isTrue = false;
            },
            getPhone() {
                wx.makePhoneCall({
                    phoneNumber: '0755-83257443'
                });
            },
        }
    }
</script>
<style lang="less" scoped>
page {
  background-color: #f7f7f7;
}
.container {
  width: 100%;
  height: 100%;
  background-color: #f7f7f7;
//   padding-bottom: 100rpx;
  .centent_box {
    width: 100%;
    background-color: #fff;
    box-sizing: border-box;
    padding: 0px 30rpx;
    .centent_title {
      display: flex;
      align-items: center;
      justify-content: space-between;
      width: 100%;
      height: 90rpx;
      border-bottom: 1px solid #f4f4f4;
      image {
        width: 24rpx;
        height: 12rpx;
      }
      .title {
        font-size: 30rpx;
        color: #333;
      }
    }
    .content_detail {
      padding: 20rpx 0px;
      font-size: 26rpx;
      color: #666;
      text {
        // padding: 10rpx 0px;
        line-height: 40rpx;
      }
      .text {
        display: block;
        padding-top: 20rpx;
      }
    }
  }
  .bottom {
    position: fixed;
    bottom: 0px;
    left: 0;
    width: 100%;
    height: 80rpx;
    text-align: center;
    line-height: 80rpx;
    background-color: #fff;
    font-size: 32rpx;
    color: #333;
    border-top: 1px solid #f4f4f4;
    .bot_box {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        .icon_kefu {
            width: 44rpx;
            height: 49rpx;
            display: block;
            margin-right: 20rpx;
        }
    }
    
  }
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
    height: 292rpx;
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
        color: #f7d123;
      }
    }
  }
}
</style>

