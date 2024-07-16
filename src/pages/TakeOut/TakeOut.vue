<template>
  <view>
    <view class="w-[90%] m-[5%]">
      <uv-search placeholder="请输入商品名称" v-model="searchKeyword"></uv-search>
    </view>
    <view class="border-gray-200 border-solid border-t border-b-0  pl-4 pr-2">
      <view class="flex justify-between w-full">
        <view class="text-2xl">{{ currentSuperMarket.name }}</view>
        <view class="flex items-center">
          <view class="text-blue-600">切换消费点</view>
          <uv-icon name="arrow-right" class="text-2xl"></uv-icon>
        </view>
      </view>
      <view class="flex items-center w-full mt-2">
        <view class="text-sm text-gray-600">营业时间{{ currentSuperMarket.time }}</view>
        <view class="ml-6">
          <uv-tags text="营业中" type="success" plain></uv-tags>
        </view>
      </view>
    </view>
    <view class="mt-8">
      <uv-vtabs
          :chain="chain"
          :list="currentSuperMarket.commodities"
          :height="height"
          hdHeight="100rpx"
      >
        <template v-for="(item,index) in currentSuperMarket.commodities" :key="index">
          <uv-vtabs-item :index="index">
            <view class="item flex mt-4"
                  v-for="(item2,index2) in item.goods"
                  :key="index2">
              <image :src="item2.imgSrc" class="h-24 w-24"></image>
              <view class="flex-col flex-1">
                <view class="h-12 items-center  ml-2">
                  <view class="text-xl mt-4 ">{{ item2.name }}</view>
                </view>
                <view class="flex">
                  <view class="text-lg mt-4 ml-2">￥{{ item2.price }}</view>
                  <view class="flex flex-1 justify-end items-end  mr-3">
                    <view class="mr-1" v-show="item2.count>0" @click="item2.count--">
                      <uv-icon name="minus-circle" size="24" color="#000000"></uv-icon>
                    </view>
                    <text class="text-[20px] text-center w-[40px] mr-1" v-show="item2.count>0">{{ item2.count }}</text>
                    <view class="m-0" @click="item2.count++">
                      <uv-icon name="plus-circle" size="24" color="#000000"></uv-icon>
                    </view>
                  </view>
                </view>

              </view>
            </view>
            <view
                class="gap"
                v-if="index<currentSuperMarket.commodities.length-1">
              <uv-gap bg-color="#f1f1f1" height="4"></uv-gap>
            </view>
          </uv-vtabs-item>
        </template>
        <uv-gap bg-color="#fff" height="600"></uv-gap>
      </uv-vtabs>

    </view>
  </view>
</template>
<script>
export default {
  data() {
    return {
      searchKeyword: "",
      tabValue: 0,
      currentSuperMarket: {
        name: "品谊生鲜超市",
        time: "7:00-22:00",
        commodities: [
          {
            name: "生鲜",
            goods: [
              {
                name: "牛肉",//牛肉
                price: "30",
                count: 0,
                imgSrc: "https://tse4-mm.cn.bing.net/th/id/OIP-C._L6Sg18dMGssq_exB21kKgHaE3?rs=1&pid=ImgDetMain"
              },
              {
                name: "冰鲜鸡翅中",
                price: "25",
                count: 0,
                imgSrc: "https://pic.nximg.cn/file/20160117/6770918_203309954000_2.jpg"
              }
            ]
          },
          {
            name: "蔬菜",
            goods: []
          },
          {
            name: "水果",
            goods: []
          },
          {
            name: "调料",
            goods: []
          }
        ]
      },
    };
  },
};

</script>
<style></style>