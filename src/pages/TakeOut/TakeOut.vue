<template>
  <view class="relative">
    <view class="w-[90%] m-[5%] ">
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
          :chain="true"
          :list="currentSuperMarket.commodities"
          :height="height"
          hdHeight="100rpx"
      >
        <view v-for="(item,index) in currentSuperMarket.commodities" :key="index">
          <uv-vtabs-item :index="index">
            <view class="item flex mt-4 rounded-2xl"
                  v-for="(item2,index2) in item.goods"
                  :key="index2">
              <image :src="item2.imgSrc" class="h-24 w-24 rounded-lg"></image>
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
        </view>
        <uv-gap bg-color="#fff" height="300"></uv-gap>
      </uv-vtabs>
    </view>
    <view class="flex absolute bottom-0 z-50 w-full h-20 ">
      <view class="flex w-3/5 h-full bg-gray-100">
        <uv-icon name="shopping-cart" size="70"></uv-icon>
        <view class="w-6 h-6 bg-red-500 rounded-full text-white text-lg text-center align-middle items-center">
          {{ sumCount() }}
        </view>
        <view class="flex flex-1 right-0 text-right text-2xl items-center align-middle justify-end">
          <text>
            ￥{{ sumPrice() }}
          </text>
        </view>
      </view>
      <view class="flex-1 bg-gray-800  flex items-center justify-center" >
        <text class="text-white text-2xl mb-5">去购物车</text>
      </view>
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
            goods: [{
              name: "番茄",
              price: "1.98",
              count: 0,
              imgSrc: "https://th.bing.com/th/id/OIP.bJ88-3D6wfLsvjAojVZSCgHaHa?w=174&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7"
            },
              {
                name: "生菜",
                price: "1.98",
                count: 0,
                imgSrc: "https://th.bing.com/th/id/OIP.gmR7yetDhEegaQERozwCTwHaGt?w=185&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7"
              }]
          },
          {
            name: "水果",
            goods: [
              {
                name: "苹果",
                price: "5.98",
                count: 0,
                imgSrc: "https://th.bing.com/th/id/OIP.HTN-sUDdcgATz6BiZn5yeQHaH7?w=158&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7"
              },
              {
                name: "梨",
                price: "3.48",
                count: 0,
                imgSrc: "https://th.bing.com/th/id/OIP.l597RB9vwFOSC1JTKmB6JwHaHa?w=174&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7"
              }
            ]
          },
          {
            name: "调料",
            goods: [{
              name: "盐",
              price: "1.5",
              count: 0,
              imgSrc: "https://th.bing.com/th/id/OIP.7BO7vqejFo2iY7XYoysInwHaHa?w=195&h=195&c=7&r=0&o=5&dpr=1.3&pid=1.7"
            },
              {
                name: "生抽",
                price: "1.98",
                count: 0,
                imgSrc: "https://th.bing.com/th/id/OIP.O9x69xZK6UwxQAq5S7mtswHaHa?w=180&h=180&c=7&r=0&o=5&dpr=1.3&pid=1.7"
              }]
          }
        ]
      },
    };
  },
  computed: {
    height() {
      return uni.getSystemInfoSync().windowHeight - uni.upx2px(300);
    }
  },
  methods: {
    sumPrice() {
      let sum = 0;
      this.currentSuperMarket.commodities.forEach((commodity) => {
        commodity.goods.forEach((good) => {
          sum += good.count * good.price;
        })
      })
      return sum
    },
    sumCount() {
      let sum = 0;
      this.currentSuperMarket.commodities.forEach((commodity) => {
        commodity.goods.forEach((good) => {
          sum += good.count;
        })
      })
      return sum
    },
  },
};

</script>
<style></style>