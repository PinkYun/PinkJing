<template>
  <div>
    <map id="myMap" show-location="true" :latitude="latitude" :longitude="longitude" :controls="controls" scale="18" class="map" @end="bindregionchange"
 @begin="bindregionchange" @regionchange="bindregionchange" name="">
    <cover-image src="/static/images/dingwei.png" @tap="getLocation" class="dingwei" alt=""></cover-image>
    <cover-view class="top_box">
      <cover-view class="top">
        <cover-view class="input_box">
          <cover-image class="search_img" src="/static/images/search.png" alt=""></cover-image>
          <cover-view class="title">搜索位置查找附近的柠檬小宝</cover-view>
        </cover-view>
        <cover-image @tap="toNearList" class="list" src="/static/images/shop-list.png" alt=""></cover-image>
      </cover-view>
    </cover-view>
    <cover-view class="scan_box" @tap="getscan">
        <cover-view class="scan">
            <cover-image class="scan_img" src="/static/images/icon_scan.png" alt=""></cover-image>
            <cover-view class="title1">扫码租借</cover-view>
        </cover-view>
    </cover-view>
    <cover-view class="monkey_box">
      <cover-view class="wallet_box">
        <cover-view class="weijiao">余额: {{price}}元</cover-view>
        <!-- <cover-view class="weijiao">已交押金</cover-view> -->
        <cover-view class="img_box">
          <cover-image @tap="toUser" class="wallet_img" src="/static/images/user_img.png"></cover-image>
        </cover-view>
      </cover-view>
    </cover-view>
    <cover-view class="help" @tap="tohelpCenter">
      <cover-image class="help_img" src="/static/images/help_center.png"></cover-image>
    </cover-view>
    </map>
    
    

  </div>
</template>

<script>
import bus from '../../bus/bus.js'
export default {  
  
  data () {
    return {
      latitude: 22.55329,
      longitude: 113.88308,
      userinfo:'',
      windowWidth: '',
      windowHeight:'',
      markers: [],
      price: 0,
      controls:[
        {
          id: 1,
          iconPath:'/static/images/position1.png',
          position: {
            top: 20,
            width: 50,
            height: 50,
          },
          clickable: true
        }
      ]
    }
  },
  mounted(){

  },
  onReady(){
    this.mapCtx = wx.createMapContext('myMap') 
  },
  components: {
    
  },

  methods: {
    getLocation(){
      wx.getLocation({
        type: 'gcj02',
        success:res=>{
          // console.log(res)
          this.longitude =res.longitude
          this.latitude = res.latitude
          // this.mapCtx.moveToLocation();
        }
      })
    },
    getLogin (){
      this.userinfo = wx.getStorageSync('userinfo');
      if(this.userinfo){
        console.log('登录了')
      }else {
        console.log('未登录')
        wx.reLaunch({
          url: '/pages/login/main'
        })
      }
    },
    bindregionchange(e){  // 使用mpvue开发map组件中的视图移动事件 需要同时注册@end事件  @begin @regionchange事件 才可以触发
      // console.log(e)
      this.mapCtx.getCenterLocation({
        success: (result)=>{
          // console.log(result)
          this.longitude = result.longitude
          this.latitude = result.latitude
        },
        fail: ()=>{},
        complete: ()=>{}
      });
      
    },
    // 到个人中心页面
    toUser(){
      wx.navigateTo({
        url: '/pages/user/main'
      })
    },
    tohelpCenter(){
      wx.navigateTo({
        url: '/pages/helpCenter/main'
      })    
    },
    toNearList(){
      wx.navigateTo({
        url: '/pages/nearlist/main'
      });
    },
    // 扫码逻辑
    getscan(){      
      wx.scanCode({
        onlyFromCamera: false, //是否只能从相机扫码，不允许从相册选择图片,
        success: res => {
          // console.log(res)
          if(res.errMsg=="scanCode:ok"){
              wx.showLoading({
                title: '正在识二维码',
                mask: true,
              });
              setTimeout(() => {
                  wx.reLaunch({ url: '/pages/scanlist/main'});
                  wx.hideLoading();
              }, 2000);
              
          }
        }
      });
    }
  },

  created () {
    this.getLocation()
    this.getLogin()
    this.windowWidth = wx.getStorageSync('windowWidth')
    this.windowHeight = wx.getStorageSync('windowHeight')
    this.controls[0].iconPath = '/static/images/position1.png';
    this.controls[0].position.top = (this.windowHeight-40 )/2 ;
    this.controls[0].position.left = (this.windowWidth -40)/2 ;
    // 接手传过来的余额
    bus.$on('price',value=>{
        this.price = value
    })
  }
}
</script>

<style scoped lang="less">
.map {
  width: 100%;
  height: 100%;
  position: fixed;
}
.dingwei {
  position:absolute;
  bottom:135rpx;
  left:30rpx;
  width:96rpx;
  height:97rpx;
}
.top_box {
  position:absolute;
  top:0;
  left:0;
  width:100%;
  height:90rpx;
  background-color:#f7d123;
  padding:25rpx 32rpx;
  box-sizing:border-box;
  .top {
    display:flex;
    align-items:center;
    justify-content:space-between;
    .input_box {
      flex:1;
      margin:0 20px 0 10rpx;
      display:flex;
      margin-left:28rpx;
      align-items:center;
      .search_img {
        width: 40rpx;
        height: 40rpx;
      }
      .title {
        width:100%;
        color:#8c7300;
        font-size:30rpx;
        font-family:PingFang-SC-Medium;
        box-sizing:border-box;
        padding-left:30rpx;

      }
    }
    .list {
      width: 42rpx;
      height: 37rpx;
    }
  }
}
.scan_box {
  position:absolute;
  bottom:80rpx;
  width:200rpx;
  height:200rpx;
  background-color:#f7d123;
  border-radius:50%;
  left:50%;
  transform:translateX(-50%);
  .scan {
    width:100%;
    height:100%;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:center;
    .scan_img {
      width: 44rpx;
      height: 44rpx;
    }
    .title1 {
      font-size:28rpx;
      color:#111;
      margin-top:28rpx;
      font-family:PingFang-SC-Medium;

    }
  }
}
.monkey_box {
  position:absolute;
  bottom:280rpx;
  right:30rpx;
  width:100rpx;
  height:140rpx;
  .wallet_box {
    display:flex;
    flex-direction:column;
    width:100%;
    height:100%;
    .weijiao {
      width:100rpx;
      height:36rpx;
      line-height:36rpx;
      background-color:#fd5153;
      color:#fff;
      border-radius:18rpx;
      font-size:20rpx;
      font-family:PingFang-SC-Medium;
      text-align:center;

    }
    .img_box {
      display:block;
      line-height:1.2;
      overflow:hidden;
      white-space:nowrap;
      pointer-events:auto;
      .wallet_img {
        width:96rpx;
        height:97rpx;

      }
    }
  }
}
.help {
  position:absolute;
  right:30rpx;
  bottom:135rpx;
  .help_img {
    width: 100rpx;
    height: 100rpx;
  }
}
</style>
