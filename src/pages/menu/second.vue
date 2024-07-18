<template>
  <view>
    <video class="w-full h-60" id="myVideo" :src="videoSrc"/>
    <view class="flex-col ml-2">
      <view class="ml-6 mr-6 mt-4 text-2xl font-bold">{{ t }}</view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {

      t: "",
      videoSrc: "https://qiniu-web-assets.dcloud.net.cn/unidoc/zh/2minute-demo.mp4",
    };
  },
  methods: {},
  onLoad(option) {
    let _this = this;
    console.log(option.name);
    uni.setNavigationBarTitle({
      title: option.name
    });
    uni.request({
      url: 'http://47.109.98.51:8080/second/1?name=' + option.name,
      success: (res) => {
        _this.t = res.data.text;
        _this.videoSrc = res.data.videoSrc ? res.data.videoSrc : _this.videoSrc;
        console.log(res.data);
      }
    })
  }
}
</script>