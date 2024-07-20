<template>
  <view class="w-full h-full">
    <view v-show="isEmpty()">
      <view class=" justify-center items-center h-full">
        <view class="text-center">
          <image src="https://img0.baidu.com/it/u=3818538838,755962273&fm=253&fmt=auto&app=138&f=PNG?w=383&h=658"
                 mode="aspectFill" class="w-full h-96"></image>
          <text class="text-2xl font-bold">暂无历史记录</text>
        </view>
      </view>
    </view>
    <view v-show="!isEmpty()">
      <view v-for="(item, index) in historyList " :key="index"
            class="container mx-auto max-w-screen-lg shadow-lg p-6 h-28 mt-5 rounded-2xl	" style="width: 80%;">
        <view class="relative flex items-center space-x-4" style="height: 100%;"
              @click="handleOnclick(item)"
        >
          <view class="flex items-center justify-center">
            <image :src="item.image" class="h-32 w-52 rounded-2xl"></image>
          </view>
          <view class="ml-10">
            <view>
              <!-- 使用 'absolute top-0 right-0' 定位到右上角 -->
              <text class="text-lg">{{ item.text }}</text>
            </view>
            <view class="absolute bottom-0 right-0 text-xs text-sky-500">
              <!-- 使用 'absolute bottom-0 right-0' 定位到右下角 -->
              <text>查看详情 ></text>
            </view>
          </view>
        </view>
      </view>

    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      historyList: [],
    };
  },
  onShow() {
    console.log("历史记录onshow")
    this.historyList = JSON.parse(uni.getStorageSync('historyList') ? uni.getStorageSync('historyList') : "[]")
    console.log(uni.getStorageSync('historyList'))
  },
  methods: {
    isEmpty() {
      let arr = this.historyList
      return !arr || arr.length === 0
    },
    handleOnclick(item) {
      uni.navigateTo({
        url: '/pages/menu/second?name=' + item.text
      });
    },
  }
}
</script>

<style lang="scss">

</style>
