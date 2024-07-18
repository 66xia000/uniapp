<template>
  <view class="bg-gray-100 min-h-96">
    <view class="w-full bg-white">
      <view class="w-[95%] ml-[2.5%] mr-[2.5%]">
        <uv-search placeholder="请输入消费点名称" v-model="searchKeyword"></uv-search>
      </view>
    </view>
    <view v-for="superMarket in SuperMarketList"
          class="bg-white w-[95%] m-[2.5%]  rounded-lg"
    >
      <view class="flex justify-between w-full">
        <view class="text-2xl">{{ superMarket.name }}</view>
        <view class="flex items-center">
          <view class="text-blue-600">去下单</view>
          <uv-icon name="arrow-right" class="text-2xl"></uv-icon>
        </view>
      </view>
      <view class="flex">
        <view v-for="tag in superMarket.tags1" class=" mt-1 mr-3">
          <uv-tags :text="tag" plain color="#AAA" borderColor="#AAA"></uv-tags>
        </view>
      </view>
      <view class="flex mt-3">
        <view class="text-xs text-gray-400 mr-1">营业时间</view>
        <view class="text-xs text-gray-400 mr-1">{{ superMarket.shopTime }}</view>
      </view>
      <view>
        <view class="text-xs text-gray-400 mr-1">特色食材：</view>
        <uv-grid :border="false" col="5">
          <uv-grid-item v-for="(tag,index) in superMarket.tags2" :key="index">
            <view class="left-0  mt-2">
              <uv-tags  :text="tag" plain plain-fill color="#AAA" borderColor="#AAA"></uv-tags>
            </view>
          </uv-grid-item>
        </uv-grid>
      </view>
    </view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      searchKeyword: "",
      SuperMarketList: [
        {
          name: '品谊生鲜超市',
          tags1: ["生鲜", "蔬菜", "水果"],
          tags2: ["猪肋排", "牛肉", "三黄鸡", "卤蛋", "有机蔬菜", "进口水果", "手工面包", "本地蜂蜜", "有机牛奶", "进口红酒", "特色咖啡", "天然燕麦", "进口奶酪"],
          shopTime: '08:00-22:00',
        },
      ]
    };
  }
}
</script>

<style lang="scss">

</style>
