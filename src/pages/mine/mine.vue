<template>
    <view class="container mx-auto max-w-screen-lg shadow-lg rounded-lg p-6 h-20 mt-5" style="width: 80%;">
        <view class="flex items-center space-x-4">
            <view>
                <image :src="avatarUrl" class="avatar rounded-full h-20 w-20"></image>
            </view>
            <view>
                <view v-if="flag" class="ml-20 w-40">
                    <uv-button type="primary" text="登录" class="avatar-wrapper w-40" open-type="chooseAvatar"
                        @chooseavatar="onChooseAvatar"></uv-button>
                </view>

                <view v-else class="ml-20">
                    <input v-if="f" type="nickname" class="weui-input" placeholder="点击获取昵称" />
                </view>
            </view>



        </view>
    </view>



</template>

<script>
export default {
    data() {
        return {
            flag: true,
            f: true,
            avatarUrl: 'https://mmbiz.qpic.cn/mmbiz/icTdbqWNOwNRna42FI242Lcia07jQodd2FJGIYQfG0LAJGFxM4FbnQP6yfMxBgJ0F3YRqJCJ1aPAK2dQagdusBZg/0'
        }
    },
    methods: {
        onChooseAvatar(res) {
            this.avatarUrl = res.avatarUrl
            this.flag = false;
        }
    }
}

</script>