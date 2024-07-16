<template>
  <view>
    <text>扫码结果{{ res }}</text>
    <button @click="scanCode">点击扫码</button>
  </view>
</template>

<script>
export default {
  data() {
    return {
      res: ""
    };
  },
  methods: {
    scanCode() {
      let _this = this
      uni.scanCode({
        success: function (res) {
          _this.res = res.result
        }
      });
    }
  },
}
</script>

<style lang="scss">

</style>
