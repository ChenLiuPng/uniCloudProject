<template>
	<view class="vivify fadeIn delay-250">
		<!-- 标题 -->
		<view class="title main-color font-weight-bold h2 flex align-center justify-center">
			Welcome back!
		</view>
		<!-- 表单域 -->
		<uni-forms ref="forms" class="forms" :value="forms" :rules="rules">
			<uni-forms-item name="username">
				<uni-easyinput v-model="forms.username" class="input-bg-color py-2 rounded" :inputBorder="false" placeholder="账号" />
			</uni-forms-item>
			<uni-forms-item name="password">
				<uni-easyinput v-model="forms.password" class="input-bg-color py-2 rounded" :inputBorder="false" placeholder="密码" type="password" />
			</uni-forms-item>
			<view class="text-center secondary-color position-relative">
				<view @tap="toRegisterPage">注册新用户?</view>
				<view class="line position-absolute"></view>
			</view>
		</uni-forms>
		<view class="cover bg-white"></view>
		<view class="bg-image flex align-center justify-center">
			<view class="iconfont icon-jiantou text-white login-button" @click="login"></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				forms: {
					username: '',
					password: ''
				},
				rules: {
					username: {
						rules: [{
							required: true,
							errorMessage: '请输入{label}',
						}, {
							minLength: 2,
							maxLength: 10,
							errorMessage: '{label}长度{minLength}到{maxLength}',
						}],
						label: "账号"
					},
					password: {
						rules: [{
							required: true,
							errorMessage: '请输入{label}',
						}, {
							minLength: 8,
							maxLength: 16,
							errorMessage: '{label}长度在{minLength}到{maxLength}',
						}, {
							pattern: /^(?=.*[a-z])(?=.*[A-Z])[a-zA-Z0-9~!@&%#_]{8,16}$/,
							errorMessage: "{label}必须包含大小写字母"
						}],
						label: "密码"
					}
				},
			}
		},
		methods: {
			 async login(){
				 // TODO
				try{
					const forms = await this.$refs.forms.validate();
					console.log(forms);
				}catch(e){
					//TODO handle the exception
					console.log('校验失败');
				}
			},
			toRegisterPage(){
				uni.navigateTo({
					url:'/pages/register/register',
					animationType:'slide-in-bottom'
				})
			}
		}
	}
</script>

<style scoped>
	.title {
		height: 40vh;
	}

	.forms {
		height: 25vh;
	}

	.line {
		width: 180rpx;
		height: 2.5px;
		background-color: var(--secondary-color);
		left: 50%;
		transform: translateX(-50%);
		bottom: -6px;
	}

	.cover {
		height: 10vh;
		border-radius: 0 0 50% 50%;
		transform: translateY(60%);
	}

	.bg-image {
		height: 30vh;
		background-image: url(@/static/login/bg.jpg);
		background-size: cover;
		background-position: bottom;
	}

	.login-button {
		font-size: 140rpx;
	}
</style>
