<template>
  <button v-for="(value,i) in test" class="flex flex-col justify-center align-middle text-cyan-500"
          v-show="i%2===0"

  >{{ value }}的索引是{{ i }}
  </button>

</template>

<script>
export default {
  setup() {
    return {
      test: [1, 2, 3, 4, 5, 6, 7, 8],
    }
  },
  methods: {

  },
  onLoad() {

  },
}
</script>

<style>

</style>