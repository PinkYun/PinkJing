<script>
export default {
  created () {
    // 调用API从本地缓存中获取数据
    const logs = wx.getStorageSync('logs') || []
    logs.unshift(Date.now())
    wx.setStorageSync('logs', logs)

    console.log('app created and cache logs by setStorageSync');
    // getdeviveinfo(){
      let res = wx.getSystemInfoSync();
      wx.setStorageSync('windowWidth',res.windowWidth);
      wx.setStorageSync('windowHeight',res.windowHeight);
    // }
  }
}
</script>

<style>
@import './common/iocnfont/iconfont.css';
</style>
