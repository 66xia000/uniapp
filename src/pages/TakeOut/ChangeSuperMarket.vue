<template>
  <view class="bg-gray-100 min-h-96">
    <view class="w-full bg-white">
      <view class=" bg-gray-100 w-[95%] ml-[2.5%] mr-[2.5%]">
        <uv-search placeholder="请输入消费点名称" v-model="searchKeyword"></uv-search>
      </view>
    </view>
    <view class=" bg-white w-[95%] ml-[2.5%] mr-[2.5%] ">
      <view v-for="superMarket in SuperMarketList"
            class="bg-white w-7/8 m-6 rounded-lg"
            @click="goToTakeOut(superMarket.name)"
            v-show="isShow(superMarket.name)"
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
          <uv-grid :border="false" col="4">
            <uv-grid-item v-for="(tag,index) in superMarket.tags2" :key="index">
              <view class="left-0  mt-2">
                <uv-tags :text="tag" plain plain-fill color="#AAA" borderColor="#AAA"></uv-tags>
              </view>
            </uv-grid-item>
          </uv-grid>
        </view>
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
        {
          name: '乐购生活超市',
          tags1: ["零食", "饮料", "日用品"],
          tags2: ["薯片", "可乐", "洗发水", "牙膏", "洗衣液", "卫生纸", "卫生巾", "婴儿奶粉", "儿童玩具", "家用电器", "电子产品"],
          shopTime: '09:00-21:00',
        },
        {
          name: '绿野有机超市',
          tags1: ["有机食品", "健康食品", "无添加"],
          tags2: ["有机大米", "有机面粉", "有机鸡蛋", "有机蔬菜", "有机水果", "有机肉类", "有机奶制品", "有机蜂蜜", "有机茶叶", "有机咖啡"],
          shopTime: '08:30-21:30',
        },
        {
          name: '优选进口超市',
          tags1: ["进口食品", "进口日用品", "进口酒类"],
          tags2: ["进口巧克力", "进口饼干", "进口橄榄油", "进口红酒", "进口啤酒", "进口果汁", "进口咖啡", "进口茶叶", "进口奶粉", "进口护肤品"],
          shopTime: '10:00-20:00',
        },
        {
          name: '健康生活超市',
          tags1: ["健康食品", "运动用品", "营养品"],
          tags2: ["蛋白粉", "维生素", "矿物质补充剂", "运动饮料", "运动装备", "健身器材", "健康零食", "低脂食品", "无糖食品", "低钠食品"],
          shopTime: '09:00-22:00',
        }
      ]
    };
  },
  methods: {
    goToTakeOut(){
      uni.navigateBack()
    },
    isShow(name){
      return name.includes(this.searchKeyword)
    }
  }
}
</script>

<style lang="scss">

</style>
