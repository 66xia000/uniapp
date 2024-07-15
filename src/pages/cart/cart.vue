<template>
  <view>
    <view class="flex">
      <view v-for="(item,index) in topArr" :key="index" class="ml-2">
        <image :src="item.icon" class="w-[100px] h-[100px]"></image>
        <view>{{ item.name }}</view>
        <view>{{ item.price/100 }}</view>
        <button @click="addGoodsToBottomArr(item)">+</button>
      </view>
    </view>
    <scroll-view class="justify-center align-middle w-full h-3/4" >
      <view v-for="(item,index) in bottomArr" :key="index" class="mt-2 ">
        <image :src="item.icon" class="w-[100px] h-[100px]"></image>
        <view>{{ item.name }}</view>
        <view>{{ item.price / 100 }}</view>
        <view class="flex">
          <button :disabled="item.count<=1" @click="item.count--">-</button>
          <view>{{ item.count }}</view>
          <button @click="item.count++">+</button>
        </view>

      </view>
    </scroll-view>
    <view>总价是{{ totalPrice()/100 }}----数量是{{totalCount()}}</view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      topArr: [
        {
          count: 1,
          name: "苹果",
          icon: "https://ts1.cn.mm.bing.net/th?id=ODLS.72dbb4f0-dec8-4f7b-99f2-5bb5bca96a8b&w=32&h=32&qlt=90&pcl=fffffa&o=6&pid=1.2",
          price: 4199,
          originalprice: 4599
        },
        {
          count: 1,
          name: "华为",
          icon: "https://ts3.cn.mm.bing.net/th?id=ODLS.98d8b523-d420-4ef7-9a4b-a503cd604ed0&w=32&h=32&qlt=90&pcl=fffffa&o=6&pid=1.2",
          price: 4299,
          originalprice: 4599
        },
        {
          count: 1,
          name: "小米",
          icon: "https://ts2.cn.mm.bing.net/th?id=ODLS.a87600cc-8f84-4d93-a78b-6bdf6981c0b8&w=32&h=32&qlt=90&pcl=fffffa&o=6&pid=1.2",
          price: 4299,
          originalprice: 4599
        },
        {
          count: 1,
          name: "oppo",
          icon: "https://ts4.cn.mm.bing.net/th?id=ODLS.92dab5e1-e371-44a7-813d-a223ec3483bf&w=32&h=32&qlt=90&pcl=fffffa&o=6&pid=1.2",
          price: 4299,
          originalprice: 4599
        },
      ],
      bottomArr: [],
    };
  },
  methods: {
    addGoodsToBottomArr(v) {
      let flag = false
      this.bottomArr.forEach((item, index) => {
        if (v.name == item.name) {
          item.count += 1
          flag = true
        }
      })
      if (!flag)
        this.bottomArr.push(v)
    },
    totalPrice() {
      let sum = 0.0
      this.bottomArr.forEach((item, index) => {
        sum += item.count * item.price
      })
      return sum
    },
    totalCount() {
      let count = 0
      this.bottomArr.forEach((item, index) => {
        count += item.count
      })
      return count
    }
  },
}
</script>

<style lang="scss">

</style>
