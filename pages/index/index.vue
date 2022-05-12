<template>
	<view>
		<view class="text-center bg-danger text-white vivify delay-1000" :class="diyClass">
			{{title}}
		</view>
		<button @click="diyClassChange">
			动画
		</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				diyClass: ''
			}
		},
		onLoad() {

		},
		methods: {
			diyClassChange() {
				if(!this.diyClass){
					this.diyClass = 'flipOutX'
				}else{
					this.diyClass = ''
				}
			}
		}
	}
</script>

<style>

</style>
