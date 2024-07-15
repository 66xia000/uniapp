<template>
  <view>
    <view class="relative">
      <view class="w-[95%] absolute h-[50px] bg-transparent z-50 flex ml-[2%] items-center">
        <uv-search placeholder="不要用贝壳" shape="round"></uv-search>
        <view class=" justify-center flex text-gray-500">
          <text>{{ city }}</text>
          <uv-icon name="map"></uv-icon>
          <text>/{{ weather }}</text>
          <text>/{{ temperature }}°C</text>
        </view>
      </view>
      <uv-swiper :list="list">

      </uv-swiper>
    </view>
  </view>

</template>

<script>
export default {
  data() {
    return {
      list: [
        'https://cdn.uviewui.com/uview/swiper/swiper1.png',
        'https://cdn.uviewui.com/uview/swiper/swiper2.png',
        'https://cdn.uviewui.com/uview/swiper/swiper3.png',
      ],
      city: "定位中",
      weather: "未知",
      temperature: "26",
    }
  },
  methods: {},
  onLoad() {
    let _this = this
    let key = "f772f4994eef66489335ef6c6769e269"; // 你自己的key
    uni.getLocation({
      type: 'wgs84',
      success: function (res) {
        let longitude = res.longitude; // 经度
        let latitude = res.latitude;  // 纬度
        uni.request({
          url: `https://restapi.amap.com/v3/geocode/regeo?key=${key}&location=${longitude},${latitude}&poitype=&radius=&extensions=all&roadlevel=0`, // 高德地图
          success: (res) => {
            _this.city = res.data.regeocode.addressComponent.city;  // 城市赋值
            let adcode = res.data.regeocode.addressComponent.adcode;  // 保存城市编码
            // 发送第二个请求获取天气
            uni.request({
              url: `https://restapi.amap.com/v3/weather/weatherInfo?key=${key}&city=${adcode}`, // 获取天气的地址。
              success: (res) => {
                _this.weather = res.data.lives[0].weather; // 天气赋值
                _this.temperature = res.data.lives[0].temperature; // 温度赋值
              }
            });
          }
        });
      }
    });
  },
}
</script>

<style>

</style>