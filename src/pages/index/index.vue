<template>
  <view>
    <view class="relative">
      <view class="w-[90%] absolute h-[50px] bg-transparent z-50 flex ml-[2%]">
        <uv-search placeholder="不要用贝壳" shape="round" ></uv-search>
        <view class="text-justify flex">
          <text class="text-center">{{city}}</text>
          <uv-icon name="map"></uv-icon>
          <text>{{weather}}</text>
          <text>{{temperature}}°C</text>
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
      city:"成都",
      weather:"雨",
      temperature:"26",
    }
  },
  methods: {},
  onLoad() {

  },
}
</script>

<style>

</style>