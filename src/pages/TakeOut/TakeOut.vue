<template>
  <view class="relative">
    <view class="w-[90%] m-[5%] ">
      <uv-search placeholder="请输入商品名称" v-model="searchKeyword"></uv-search>
    </view>
    <view class="border-gray-200 border-solid border-t border-b-0  pl-4 pr-2">
      <view class="flex justify-between w-full">
        <view class="text-2xl">{{ currentSuperMarket.name }}</view>
        <view class="flex items-center" @click="handleChangeSuperMarket">
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
    <view class="mt-4">
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
                  :key="index2"
                  v-show="isShow(item2.name)"
            >
              <image :src="item2.imgSrc" class="h-24 w-24 rounded-lg"></image>
              <view class="flex-col flex-1">
                <view class="h-12 items-center  ml-2">
                  <view class="text-xl mt-4 ">{{ item2.name }}</view>
                </view>
                <view class="flex">
                  <view class="text-lg mt-4 ml-2">￥{{ item2.price/100 }}</view>
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
    <view class="flex absolute bottom-0 z-50 w-full h-16 ">
      <view class="flex w-3/5 h-full bg-gray-100">
        <uv-icon name="shopping-cart" size="70"></uv-icon>
        <view class="w-6 h-6 bg-red-500 rounded-full text-white text-lg text-center align-middle items-center">
          {{ sumCount() }}
        </view>
        <view class="flex flex-1 right-0 text-right text-2xl items-center align-middle justify-end">
          <text class="mr-3">
            ￥{{ sumPrice()/100 }}
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
                price: 3000,
                count: 0,
                imgSrc: "https://tse4-mm.cn.bing.net/th/id/OIP-C._L6Sg18dMGssq_exB21kKgHaE3?rs=1&pid=ImgDetMain"
              },
              {
                name: "冰鲜鸡翅中",
                price: 2500,
                count: 0,
                imgSrc: "https://pic.nximg.cn/file/20160117/6770918_203309954000_2.jpg"
              }
            ]
          },
          {
            name: "蔬菜",
            goods: [{
              name: "番茄",
              price: 198,
              count: 0,
              imgSrc: "https://img2.baidu.com/it/u=1665673006,3467521838&fm=253&fmt=auto&app=120&f=JPEG?w=608&h=413"
            },
              {
                name: "生菜",
                price: 298,
                count: 0,
                imgSrc: "https://img0.baidu.com/it/u=4067688365,2264267211&fm=253&fmt=auto&app=138&f=JPEG?w=600&h=400"
              }]
          },
          {
            name: "水果",
            goods: [
              {
                name: "苹果",
                price: 598,
                count: 0,
                imgSrc: "https://img2.baidu.com/it/u=994163525,1909556555&fm=253&fmt=auto&app=120&f=JPEG?w=500&h=500"
              },
              {
                name: "梨",
                price: 348,
                count: 0,
                imgSrc: "https://img1.baidu.com/it/u=3619610546,4124687208&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=1422"
              }
            ]
          },
          {
            name: "调料",
            goods: [{
              name: "盐",
              price: 150,
              count: 0,
              imgSrc: "https://img0.baidu.com/it/u=254192677,3597287513&fm=253&fmt=auto&app=120&f=JPEG?w=750&h=500"
            },
              {
                name: "生抽",
                price: 198,
                count: 0,
                imgSrc: "https://img0.baidu.com/it/u=3304284258,4141768077&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500"
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
    handleChangeSuperMarket(){
      uni.navigateTo({
        url: '/pages/TakeOut/ChangeSuperMarket'
      })
    },
    isShow(name){
    return name.includes(this.searchKeyword)
    }
  },
};

</script>
<style></style>