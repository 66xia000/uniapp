<template>
    <text>{{ t }}</text>
</template>

<script>
export default {
    data() {
        return {
            
            t: ""
        };
    },
    methods: {

    },
    onLoad(option) {
        let _this = this;
        console.log(option.name);
        uni.setNavigationBarTitle({
            title: option.name
        });
        uni.request({
        url: 'http://47.109.98.51:8080/second/1?name='+option.name,
        success: (res) => {
          _this.t=res.data.text;
          console.log(res.data);   
        }
      })
    }
}
</script>