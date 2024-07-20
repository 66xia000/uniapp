<template>
  <view v-for="(item, index) in ll " :key="index"
        class="container mx-auto max-w-screen-lg shadow-lg p-6 h-28 mt-5 rounded-2xl	" style="width: 80%;">
    <view class="relative flex items-center space-x-4" style="height: 100%;"
          @click="handleOnclick(item) "
    >
      <!-- 添加了 'relative' 和 'height: 100%' -->
      <view class="flex items-center justify-center">
        <image :src="item.image" class="h-32 w-44 rounded-2xl"></image>
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
</template>

<script>
export default {
  data() {
    return {
      ll: []
    };
  },
  methods: {
    handleOnclick(item) {
      let historyList = JSON.parse(uni.getStorageSync("historyList")?uni.getStorageSync("historyList"):"[]")
      if (historyList.findIndex((e) => e.text === item.text)===-1)
        historyList.push(item)
      uni.setStorageSync("historyList",JSON.stringify(historyList))
      uni.navigateTo({
        url: '/pages/menu/second?name=' + item.text
      });
    },
    // 在这里定义你的方法
  },
  onLoad() {
    let _this = this;
    uni.request({
      url: 'http://47.109.98.51:56882/123/1', //仅为示例，并非真实接口地址。
      success: (res) => {
        _this.ll = res.data;
      }
    })
  }
};
</script>