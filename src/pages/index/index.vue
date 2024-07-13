<template>
  <view class="content">
    <image class="logo" src="/static/logo.png" />
    <view class="text-area">
      <text class="title">{{ title }}</text>
      <!-- 直接从 store 中访问 state -->
      <text>Current Count: {{ counter.count }}</text>
    </view>
    <view class="w-full h-[100px] bg-[red] flex justify-center items-center">
      <text>Hello Tailwind CSS</text>
    </view>
    <view>
      <uv-button type="primary" text="uv-ui按钮"></uv-button>
    </view>
  </view>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useCounterStore } from '@/stores/counter'

const title = ref('Hello')
const counter = useCounterStore();
counter.count++
// 自动补全！ 
counter.$patch({ count: counter.count + 1 })
// 或使用 action 代替
counter.increment()
</script>

<style>
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.logo {
  height: 200rpx;
  width: 200rpx;
  margin-top: 200rpx;
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 50rpx;
}

.text-area {
  display: flex;
  justify-content: center;
}

.title {
  font-size: 36rpx;
  color: #8f8f94;
}
</style>
