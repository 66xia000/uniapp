<template>
  <view>
    <view class="flex justify-around mt-3">
      <image src="/static/R-C.jpg" class="h-[5rem] w-[5rem]"></image>
      <image src="/static/logo.png" class="h-[5rem] w-[5rem]"></image>
      <image src="/static/R-C.jpg" class="h-[5rem] w-[5rem]"></image>
    </view>
    <button class="w-11/12 h-10 mt-10">{{buttonValue}}</button>
  </view>

</template>

<script>
export default {
  data() {
    return {
      buttonValue:"测试按钮",
      test: [1, 2, 3, 4, 5, 6, 7, 8],
    }
  },
  methods: {

  },
  onLoad() {

  },
}
</script>

<style>

</style>