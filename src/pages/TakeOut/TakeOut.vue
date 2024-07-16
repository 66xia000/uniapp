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
    <uv-vtabs :chain="chain" :list="currentSuperMarket.commodities" :barItemBadgeStyle="{ right: '20px', top: '12px' }"
      @change="change">
      <uv-vtabs-item>
        <view class="item" v-for="(item2, index2) in getGoods" :key="index2">
          <text class="text">{{ item2.name }}</text>
          <text class="text">{{ item2.price }}</text>
        </view>
      </uv-vtabs-item>
    </uv-vtabs>
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
                imgsrc: "https://tse4-mm.cn.bing.net/th/id/OIP-C._L6Sg18dMGssq_exB21kKgHaE3?rs=1&pid=ImgDetMain"
              },
              {
                name: "冰鲜鸡翅中",
                price: "25",
                imgsrc: "https://pic.nximg.cn/file/20160117/6770918_203309954000_2.jpg"
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
  computed: {
    getGoods() {
      const _list = this.list[this.value]?.childrens;
      return _list ? _list : [];
    }
  },

  methods: {
    change(index) {
      this.tabValue = index;
      // console.log(this.currentSuperMarket.commodities[this.tabValue]?.goods);
      console.log(JSON.stringify(this.currentSuperMarket.commodities[this.tabValue]?.goods));
      console.log("index changed to", index);
      console.log("getGoods ", getGoods());
    }
  }
};

</script>
<style></style>