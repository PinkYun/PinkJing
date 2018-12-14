<template>
  <div class="container">
    <div class="shop_box">
      <div class="shop_list">
        <div class="shop_l">
          <img src="/static/images/mei_img.jpg" alt>
        </div>
        <div class="shop_r">
          <div class="shop_name">田厦金牛广场</div>
          <div class="shop_address">
            <i class="iconfont icon-dingwei"></i>
            <text>南山区桃园地铁A出口</text>
          </div>
          <div class="shop_juli">
            <div class="juli_l">
              <i class="iconfont icon-NAVIGATION"></i>
              <text>213米</text>
            </div>
            <div class="juli_r">
              <text class="xian"></text>
              <div class="daohang">
                <img src="/static/images/icon_ding.png" alt>
                <text>导航</text>
              </div>
            </div>
          </div>
          <div class="shop_shebei">
            <img src="/static/images/icon_phone.png" alt>
            <text class="kejie">可借: 3</text>
            <text>可还: 2</text>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {};
  }
};
</script>
<style lang="less" scoped>
.container {
    background-color: #efeff4;
}
.shop_box {
  width: 100%;
  background-color: #efeff4;
  height: 100%;
  .tips {
    font-size: 24rpx;
    /* font-family:PingFang-SC-Medium;
    font-weight:500; */
    color: #999;
    text-align: center;
    margin-top: 80rpx;
  }
  .shop_list {
    width: 100%;
    height: 220rpx;
    background-color: #fff;
    display: flex;
    box-sizing: border-box;
    padding: 30rpx 0px;
    padding-left: 30rpx;
    margin-bottom: 20rpx;
    .shop_l {
      width: 140rpx;
      // height: 140rpx;
      margin-right: 24rpx;
      image {
        width: 100%;
        height: 100%;
      }
    }
    .shop_r {
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      // height: 140rpx;
      .shop_name {
        font-size: 32rpx;
        font-family: PingFang-SC-Medium;
        font-weight: 500;
        color: #333;
      }
      .shop_address {
        font-size: 24rpx;
        color: #999;
        display: flex;
        align-items: center;
        .iconfont {
          margin-right: 14rpx;
          font-size: 28rpx;
        }
      }
      .shop_shebei {
        display: flex;
        align-items: center;
        .iconfont {
          width: 21rpx;
          height: 30rpx;
          margin-right: 10rpx;
        }
        img {
            margin-right: 10rpx;
            width: 21rpx;
            height: 30rpx;
        }
        text {
          font-size: 24rpx;
          color: #666666;
        }
        .kejie {
          margin-right: 30rpx;
        }
      }
      .shop_juli {
        display: flex;
        height: 48rpx;
        line-height: 48rpx;
        font-size: 26rpx;
        color: #999;
        justify-content: space-between;
        .juli_l {
            flex: 1;
            display: flex;
            align-items: center;
        }
        .juli_r {
          display: flex;
          align-items: center;
          margin-right: 30rpx;
          .daohang {
            width: 140rpx;
            height: 48rpx;
            background-color: #201e2c;
            color: #fff;
            border-radius: 24rpx;
            display: flex;
            align-items: center;
            justify-content: center;
            img {
                margin-right: 10rpx;
                width: 24rpx;
                height: 20rpx;
            }
          }
        }
        .xian {
          width: 1px;
          height: 28rpx;
          background-color: #e5e5e5;
          margin-right: 30rpx;
        }
      }
    }
  }
}
</style>


