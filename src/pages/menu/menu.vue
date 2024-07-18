<template>
  <view v-for="(item, index) in ll " :key="index"
        class="container mx-auto max-w-screen-lg shadow-lg p-6 h-28 mt-5 rounded-2xl	" style="width: 80%;">
    <view class="relative flex items-center space-x-4" style="height: 100%;"
          @click="redict(item.text)"
    >
      <!-- 添加了 'relative' 和 'height: 100%' -->
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
</template>

<script>
export default {
  data() {
    return {
      ll: []
    };
  },
  methods: {
    redict(x) {
      uni.navigateTo({
        url: '/pages/menu/second?name=' + x
      });
    }
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