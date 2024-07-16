<template>
  <view class="ml-8 mt-1">
    <text class="text-xl font-bold">您好，欢迎光临！</text>
  </view>
  <view class="flex justify-center items-center overflow-hidden mt-2">
    <view class="p-4 bg-white rounded-lg shadow-md w-80">
      <img class="rounded-lg w-full" :src="imageSrc" alt="Image Description">
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
        <view v-for="(item, index) in ll" :key="index" class="mr-5" >
          <image  :src="item.image" mode="heightFix" style="height: 200px;"></image>
          <view class="flex justify-center items-center">
            <text class="w-full text-center">2333</text>
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
      imageSrc: 'https://img95.699pic.com/photo/50074/0919.jpg_wh860.jpg',

      ll: [{
        image: "https://via.placeholder.com/200x200.png/3c9cff/fff"
      }, {
        image: "https://via.placeholder.com/200x200.png/f9ae3d/fff"
      }, {
        image: "https://via.placeholder.com/200x200.png/5ac725/fff"
      }, {
        image: "https://via.placeholder.com/200x200.png/f56c6c/fff"
      }, {
        image: "https://via.placeholder.com/200x200.png/909399/fff"
      }]
    };
  }
};
</script>