<template>
	<view class="page-header px-2 flex align-center justify-between">
		<view v-if="canBack" class="iconfont icon-arrowLeft-fill back-icon" @tap="back"></view>
		<view class="font-lg">
			{{title}}
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			title:{
				type:String,
				default:""
			},
			canBack:{
				type:Boolean,
				default:true
			}
		},
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
	.back-icon {
		font-size: 50rpx;
	}
	.page-header {
		height: 100rpx;
	}
</style>
