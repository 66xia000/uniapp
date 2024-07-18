<template>
    <view class="container mx-auto max-w-screen-lg shadow-lg rounded-lg p-6 h-14 mt-5 " style="width: 80%;">
        <view class="flex items-center space-x-4">

            <view class="text-1xl">如果您有任何的问题，请拨打电话给我们的程序员，相信我，那一定是程序特性，他们会解决的。</view>

        </view>
    </view>
    <view class="mt-96 flex items-center justify-center">
        <uv-button type="primary" @click="makeCall" class="w-3/4 md:w-1/2 lg:w-2/5">拨打电话</uv-button>
    </view>
</template>

<script>
export default {
    data() {
        return {
            itemList: ['00000000', '11111111', '22222222', '33333333', '44444444', '55555555'],
        }
    },
    methods: {
        makeCall() {
            uni.showActionSheet({
                itemList: this.itemList,   //itemList字段不变
                success: function (res) {
                    if (!res.cancel && res.tapIndex !== undefined) {
                        uni.makePhoneCall({
                            phoneNumber: this.itemList[res.tapIndex],
                            success: function () {
                                console.log('拨打电话成功');
                            },
                            fail: function () {
                                console.log('拨打电话失败');
                            }
                        });
                    }
                }.bind(this) // 绑定this作用域
            });
        }
    }
}
</script>
