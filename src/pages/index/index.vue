<template>
  <view>
    <view class="flex justify-around mt-3">
      <image src="/static/OIP-C.jpg" class="h-[5rem] w-[5rem]"></image>
      <image src="/static/logo.png" class="h-[5rem] w-[5rem]"></image>
      <image src="/static/OIP-C.jpg" class="h-[5rem] w-[5rem]"></image>
    </view>
    <view v-for="item in info" class="flex">
      <view>姓名：{{ item.name }}</view>
      <view>年龄：{{ item.age }} </view>
      <view>性别：{{ item.sex }} </view>
    </view>
    <button class="w-11/12 h-10 mt-10">{{ buttonValue }}</button>
    <button class="w-11/12 h-10 mt-4"
            v-for="(value,key) in testArr" :key="key"
            v-show="key%2===0"
    >按钮{{ value }}的位置是{{ key }}
    </button>
    <button @click="()=>{showButton=!showButton}">点击改变按钮的显隐</button>
    <button v-show="showButton">受上面的按钮控制</button>
    <button @click="()=>{whichIMG=!whichIMG}">改变图片</button>
    <image :src="whichIMG?img1:img2"></image>
  </view>

</template>

<script>
export default {
  data() {
    return {
      whichIMG:true,
      img1:"https://img.zcool.cn/community/01eafb5d2b3736a8012148379339e3.jpg@3000w_1l_0o_100sh.jpg",
      img2:"https://img95.699pic.com/photo/50074/0919.jpg_wh860.jpg",
      buttonValue: "测试按钮",
      testArr: [1, 2, 3, 'a', 'b', 'c'],
      showButton: true,
      info: [
        {name: "柳文涛", age: 1, sex: "Null"},
        {name: "郑鸿洋", age: 2, sex: "男"},
        {name: "李雅权", age: 3, sex: "男"},
      ]
    }
  },
  methods: {},
  onLoad() {

  },
}
</script>

<style>

</style>