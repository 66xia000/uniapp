<template>
  <view>
    <view class="relative">
      <view class="w-[95%] absolute h-[100px] bg-transparent z-50 flex ml-[2%] items-center">
        <uv-search placeholder="不要用贝壳" shape="round"></uv-search>
        <view class=" justify-center flex text-gray-500">
          <text>{{ city }}</text>
          <uv-icon name="map"></uv-icon>
          <text>/{{ weather }}</text>
          <text>/{{ temperature }}°C</text>
        </view>
      </view>
      <uv-swiper class="h-full" :list="list">

      </uv-swiper>
    </view>
    <view class="bg-transparent mt-5">
      <uv-grid :border="false" col="5">
        <uv-grid-item v-for="(item, index) in baseList" :key="index">
          <image :src="'../../static/icons/grid/' + index % 6 + '.png'"
                 :class="{ 'w-[60px] h-[60px]': index < 5, 'w-[40px] h-[40px]': index >= 5 }"/>
          <text class="grid-text mb-1 text-1xl">{{ item.title }}</text>
        </uv-grid-item>
      </uv-grid>
    </view>
    <view class="m-auto  w-[90%] h-40 shadow-lg search-house"
          style="background-image: url('../../static/icons/background.png')">
      <view class="text-2xl m-2">帮我找房</view>
    </view>
    <view>
      <view class="text-2xl m-2">本周热门好房推荐</view>
      <uv-grid :border="false" col="3">
        <uv-grid-item v-for="(item, index) in houseList" :key="index" class="ml-0.5">
          <image :src="item.imagesrc" class="w-[120px] h-[80px]"/>
          <view class="w-full ml-2 grid-text mb-1 text-lg text-left">{{ item.name }}</view>
          <view class="w-full ml-2 grid-text mb-1 text-xs text-left text-gray-600">{{ item.area }}m²</view>
          <view class="w-full ml-2 grid-text mb-1 text-sm text-left text-red-600">{{ item.price }}/m²</view>
        </uv-grid-item>
      </uv-grid>
    </view>
    <view class="ml-2">
      <view class="text-2xl">猜你不喜欢</view>
      <view class="flex mt-4" v-for="item in likeList">
        <image class="w-36 h-24 rounded-lg" :src="item.imagesrc"></image>
        <view class="flex-1 ml-2 ">
          <view class="text-lg">{{ item.name }}{{ item.room }} {{ item.faceto }}</view>
          <view class="text-sm">{{ item.room }}/{{ item.area }}m²/{{ item.faceto }}/{{ item.name }}</view>
          <view class="flex">
            <view v-for="tag in item.tags" class="mr-2">
              <uv-tags :text="tag" plain></uv-tags>
            </view>
          </view>
          <view class="text-xs text-gray-600">{{ item.price }}元/平</view>
        </view>

      </view>
    </view>
  </view>

</template>

<script>
export default {
  data() {
    return {
      baseList: [
        {
          name: 'photo',
          title: '二手房'
        }, {
          name: 'lock',
          title: '新房'
        }, {
          name: 'star',
          title: '租房'
        }, {
          name: 'photo',
          title: '装修'
        }, {
          name: 'lock',
          title: '家具商城'
        }, {
          name: 'star',
          title: '刘备'
        }, {
          name: 'photo',
          title: '李白'
        }, {
          name: 'lock',
          title: '韩信'
        },
      ],
      houseList: [
        {
          imagesrc: "https://ts1.cn.mm.bing.net/th/id/R-C.7362eff54c56e870c18a2126b26d9c23?rik=9if10ySst3TtbQ&riu=http%3a%2f%2fimg.zx123.cn%2fResources%2fzx123cn%2fuploadfile%2f2015%2f0910%2f20150910100439_21337.jpg&ehk=43EDk7VLby%2bA3dLs%2fPIIxej3Cs60UwiZ7rHB7eJ3zYk%3d&risl=&pid=ImgRaw&r=0",
          name: "效果测试",
          price: "20000",
          area: "100-300",
        },
      ],
      likeList: [{
        name: "上海花园(高新)",
        room: "2室2厅",
        faceto: "南",
        imagesrc: "https://ke-image.ljcdn.com/lease-image/house/69573aba991b7c539d40416a3c20cc36.jpeg.250x182.jpg",
        area: "108.78",
        price: "22891",
        tags: ["近地铁", "满五年", "VR看房"]
      },
        {
          name: "北京阳光小区",
          room: "3室1厅",
          faceto: "东",
          imagesrc: "https://ke-image.ljcdn.com/110000-inspection/pc1_41SgFFVXf.jpg!m_fill,w_250,h_182,l_fbk,o_auto",
          area: "95.00",
          price: "18000",
          tags: ["学区房", "新装修", "交通便利"]
        },
        {
          name: "广州蓝海公寓",
          room: "2室2厅",
          faceto: "南",
          imagesrc: "https://ke-image.ljcdn.com/lease-image/house/4d47129faa1f2db6f1b81ac42d4abf33.jpeg.250x182.jpg",
          area: "85.00",
          price: "26000",
          tags: ["海景房", "近商圈", "智能家居"]
        },
        {
          name: "深圳科技园",
          room: "1室1厅",
          faceto: "西",
          imagesrc: "https://ke-image.ljcdn.com/rent-user-avatar/959ac3d9-f746-4f3a-a3d5-faa845333852.250x182.jpg",
          area: "65.00",
          price: "32000",
          tags: ["科技园区", "低密度", "绿化好"]
        },
        {
          name: "杭州西湖美景",
          room: "4室2厅",
          faceto: "北",
          imagesrc: "https://ke-image.ljcdn.com/wanjia/b9a6bcd18129b330dd0fb7ec8a2468a7-1717642029065/85433d827180482ab914b50495da5754.jpg.250x182.jpg",
          area: "130.00",
          price: "21000",
          tags: ["湖畔住宅", "文化氛围", "安静舒适"]
        }
      ],
      list: [
        'https://cdn.uviewui.com/uview/swiper/swiper1.png',
        'https://cdn.uviewui.com/uview/swiper/swiper2.png',
        'https://cdn.uviewui.com/uview/swiper/swiper3.png',
      ],
      city: "定位中",
      weather: "未知",
      temperature: "26",
    }
  },
  methods: {},
  onLoad() {
    let _this = this
    let key = "f772f4994eef66489335ef6c6769e269"; // 你自己的key
    uni.getLocation({
      type: 'wgs84',
      success: function (res) {
        let longitude = res.longitude; // 经度
        let latitude = res.latitude;  // 纬度
        uni.request({
          url: `https://restapi.amap.com/v3/geocode/regeo?key=${key}&location=${longitude},${latitude}&poitype=&radius=&extensions=all&roadlevel=0`, // 高德地图
          success: (res) => {
            _this.city = res.data.regeocode.addressComponent.city;  // 城市赋值
            let adcode = res.data.regeocode.addressComponent.adcode;  // 保存城市编码
            // 发送第二个请求获取天气
            uni.request({
              url: `https://restapi.amap.com/v3/weather/weatherInfo?key=${key}&city=${adcode}`, // 获取天气的地址。
              success: (res) => {
                _this.weather = res.data.lives[0].weather; // 天气赋值
                _this.temperature = res.data.lives[0].temperature; // 温度赋值
              }
            });
          }
        });
      }
    });
  },
}
</script>

<style>
.search-house {
  background-size: 130px;
  background-repeat: no-repeat;
  background-position: bottom right;
}
</style>