<template>
  <view class="ml-8 mt-1 text-center">
    <text class="text-xl font-bold text-center">您好，欢迎光临！ </text>
  </view>
  <view class="flex justify-center items-center overflow-hidden mt-2">
    <view class="p-4 bg-white rounded-lg shadow-md w-80">
      <img class="rounded-lg w-full h-40" :src="imageSrc" alt="Image Description">
    </view>
  </view>

  <view class="flex justify-center items-center mt-4">
    <view class="p-4 bg-white rounded-lg shadow-md w-80">
      <view class="mb-2">
        <text class="text-xl font-bold">小程序功能介绍</text>
      </view>
      <view>
        <text class="text-gray-700">
          本小程序可以实现菜品的菜诺做法查询功能，同时实现菜品原材料外卖功能，以便居家或聚饮的需求。
        </text>
      </view>
      <view class="mt-4 flex justify-end">
        <text class="text-blue-500 underline">详情 ></text>
      </view>
    </view>
  </view>

  <view class="flex justify-center items-center mt-4">
    <view class="p-4 bg-white rounded-lg shadow-md w-80">
      <view class="mb-2">特色菜品</view>
      <uv-scroll-list>
        <view v-for="(item, index) in ll" :key="index" class="mr-5">
          <image :src="item.image" class="w-48 h-36 rounded-3xl"></image>
          <view class="flex justify-center items-center">
            <text class="w-full text-center">{{ item.text }}</text>
          </view>
        </view>
      </uv-scroll-list>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      imageSrc: 'https://tse3-mm.cn.bing.net/th/id/OIP-C.bW2lUbkKFnLl1W3V_A876QHaEo?w=316&h=197&c=7&r=0&o=5&dpr=1.3&pid=1.7',
      ll: []
    };
  },
  onLoad() {
    let _this=this;
    uni.request({
        url: 'http://47.109.98.51:56882/123/1', //仅为示例，并非真实接口地址。
        success: (res) => {
          _this.ll=res.data;
        }
      })
  }
};
</script>