<template>
	<view>
		<c-status-bar />
		<c-page-header title="注册" :canBack="false" />
		我是注册页面
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			back(){
				uni.navigateBack({
					delta:1
				})
			}
		}
	}
</script>

<style scoped>

</style>
