<template>
  <button v-for="i in test" class="t text-cyan-500">{{i}}</button>

</template>

<script>
  export default {
		setup() {
			return {
				test : [1,2,3,4,5,6,7,8],
			}
		}
	}
</script>

<style>
.t{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>