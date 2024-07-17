<template>
    <view class="container mx-auto max-w-screen-lg shadow-lg rounded-lg p-6 h-20 mt-5" style="width: 80%;">
        <view class="flex items-center space-x-4">

            <view class="relative p-2 bg-white rounded-lg shadow-md w-40 h-40">
                <img class="absolute inset-0 object-cover rounded-lg w-40 h-20"
                    src="https://cp1.douguo.com/upload/caiku/5/b/7/yuan_5b56cbf976015fc3fa60d293331e43e7.jpg"
                    alt="Image Description">
            </view>
            <view class="ml-6">
                <view>
                    <text class="text-lg">我叫郑海洋</text>
                </view>
                <view class="mt-6">
                    <text>勿Q 2754423942</text>
                </view>
            </view>
        </view>
    </view>
</template>

<script>
export default {
    data() {
        return {

        }
    },
    methods: {
        test() {
            uni.request({
                url: 'http://localhost:8080/123/1', //仅为示例，并非真实接口地址。
                success: (res) => {
                    console.log(res.data);
                }
            });
        }
    }
}
</script>