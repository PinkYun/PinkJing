<template>
  <div class="container">
    <view class="title">租借记录</view>
    <view class="record_box">
      <view class="record_l">
        <img src="/static/images/record_img.png" alt>
        <div class="feedback" @tap="gety">异常反馈</div>
      </view>
      <div class="record_c">
        <div class="shop_name">田厦金牛广场</div>
        <div class="shop_order">订单号: 256554545</div>
        <div class="start_time">开始时间: 2018-12-12 12:12</div>
        <div class="over_time">结束时间: 2018-12-12 12:34</div>
        <div class="all_time">充电时长: 12112</div>
      </div>
      <div class="record_r">
        <div class="record_finish">
          <div class="r_top">
            <img src="/static/images/finish_img.png" alt>
            <div class="now">已完成</div>
          </div>
          <div class="r_bottom">金额: 1元</div>
        </div>
      </div>
    </view>
    <view class="record_box">
      <view class="record_l">
        <img src="/static/images/record_img.png" alt>
        <div class="feedback" @tap="gety">异常反馈</div>
      </view>
      <div class="record_c">
        <div class="shop_name">田厦金牛广场</div>
        <div class="shop_order">订单号: 256554545</div>
        <div class="start_time">开始时间: 2018-12-12 12:12</div>
        <!-- <div class="over_time">结束时间: 2018-12-12 12:34</div> -->
        <div class="all_time">充电时长: 充电中</div>
      </div>
      <div class="record_r">
        <div class="record_finish">
          <div class="r_top">
            <!-- <img src="/static/images/finish_img.png" alt> -->
            <div class="now">充电中</div>
          </div>
          <div class="r_bottom">金额: 未结算</div>
        </div>
      </div>
    </view>
    <div class="tip_box" v-show="isShow">
      <radio-group class="radio-group" @change="radioChange">
        <div class="title_tip">以下三项必选一项</div>
        <div class="radio_box" v-for="(item,index) in arr" :key="index">
          <label class="radio">
            <radio class :checked="item.checked" :value="item.name">{{item.name}}</radio>
          </label>
        </div>
      </radio-group>
      <textarea @blur="getValue1" maxlength="50">请输入描述,不允许超过50字(可填可不填)</textarea>
      <div class="button" @tap="toFeed">提 交</div>
    </div>
    <view class="mask" @tap="getfeed" v-show="isShow"></view>
  </div>
</template>
<script>
export default {
  data() {
    return {
      arr: [
        { name: "押金缴了未弹出充电宝", checked: false },
        { name: "归还后未退押金", checked: false },
        { name: "充电宝已还未结束充电", checked: false },
        { name: "归还充电宝订单未结束", checked: false }
      ],
      height: 100,
      isShow: false,
      value: '',
    };
  },
  methods: {
      gety(){
          this.isShow = true
      },
    getfeed() {
      this.isShow = false;
    },
    radioChange(e){
        // console.log(e.target.value)
        this.value = e.target.value

    },
    toFeed() {
        if(!this.value){
            wx.showToast({
                title: '请选择异常情况..',
                icon: 'none',
                duration: 1500,
                mask: false,
            });
            return;
        }
      wx.showLoading({
        title: "正在提交...",
        mask: true
      });
      setTimeout(() => {
        wx.showToast({
          title: "提交成功",
          icon: "none",
          duration: 1500,
          mask: false
        });
        wx.hideLoading();
        this.isShow = false
      }, 2000);
    }
  }
};
</script>
<style lang="less" scoped>
.container {
  width: 100%;
  height: 100%;
  background-color: #efeff4;
}
.title {
  width: 100%;
  height: 80rpx;
  line-height: 80rpx;
  color: #333;
  font-size: 28rpx;
  padding-left: 30rpx;
}
.record_box {
  width: 100%;
  padding: 40rpx 30rpx;
  height: 250rpx;
  background-color: #fff;
  display: flex;
  box-sizing: border-box;
  margin-bottom: 20rpx;
  .record_l {
    width: 140rpx;
    height: 100%;
    image {
      width: 80rpx;
      height: 80rpx;
      display: block;
      margin: 0rpx auto 20rpx;
    }
    .feedback {
      width: 120rpx;
      height: 40rpx;
      text-align: center;
      line-height: 40rpx;
      font-size: 26rpx;
      background-color: #f7d123;
      border-radius: 10rpx;
      color: #333;
    }
  }
  .record_c {
    margin-right: 74rpx;
    .shop_name {
      font-size: 30rpx;
      font-family: PingFang-SC-Medium;
      font-weight: 500;
      color: #222;
      margin-bottom: 20rpx;
    }
    .shop_order,
    .start_time,
    .over_time,
    .all_time {
      color: #999;
      font-size: 20rpx;
      // margin-bottom: 10rpx;
      height: 30rpx;
    }
  }
  .record_r {
    flex: 1;
    height: 100%;
    .record_finish {
      position: relative;
      width: 100%;
      height: 100%;
      .r_top {
        width: 100%;
        position: absolute;
        top: -40rpx;
        height: 108rpx;
        image {
          height: 100%;
          width: 134rpx;
        }
        view {
          font-size: 26rpx;
          color: #666;
          position: absolute;
          top: 50%;
          transform: translateY(-50%);
          right: 0px;
        }
        .now {
          font-size: 26rpx;
          color: #666;
          position: absolute;
          top: 50%;
          transform: translateY(-50%);
          right: 0px;
          color: #f7d123;
        }
      }
      .r_bottom {
        width: 100%;
        position: absolute;
        bottom: -2rpx;
        color: #333;
        right: 20rpx;
        font-size: 30rpx;
        white-space: nowrap;
        text {
          font-size: 32rpx;
          color: #222;
        }
      }
    }
  }
}
.tip_box {
  position: absolute;
  top: 100rpx;
  left: 50%;
  transform: translateX(-50%);
  width: 90%;
  height: 700rpx;
  box-sizing: border-box;
  padding: 0rpx 30rpx;
  background-color: #fff;
  z-index: 112;
  border-radius: 10rpx;
  .radio-group {
    padding-top: 20rpx;
    .radio {
      text-align: left;
      height: 40rpx;
      radio {
        transform: scale(0.5);
        color: #333;
        width: 100%;
        font-size: 44rpx;
        margin-left: -40rpx;
      }
    }
    .title_tip {
      line-height: 40rpx;
      font-size: 28rpx;
      color: #999;
      padding-left: 20rpx;
    }
  }
  textarea {
    margin-top: 20rpx;
    width: 90%;
    height: 200rpx !important;
    border: 1px solid #aaa;
    padding-left: 20rpx;
    font-size: 32rpx;
    padding-top: 10rpx;
  }
  .button {
    margin-top: 30rpx;
    width: 100%;
    height: 88rpx;
    background-color: #f7d123;
    text-align: center;
    line-height: 88rpx;
    font-size: 36rpx;
    color: #333;
    border-radius: 44rpx;
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
</style>

