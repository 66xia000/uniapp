<template>
    <button @click="test">123</button>
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