<template>
	<view>
		<c-status-bar />
		<c-page-header title="注册" />
		<uni-file-picker class="avatar flex align-center justify-center" v-model="avatar" return-type="object" limit="1"
			mode="grid" file-mediatype="image" :image-styles="avatarStyle">
			<view class="avatarSeat input-bg-color flex align-center justify-center">
				头像
			</view>
		</uni-file-picker>
		<uni-forms ref="forms" class="px-2 mt-3" :value="forms" :rules="rules">
			<uni-forms-item name="username">
				<uni-easyinput v-model="forms.username" class="input-bg-color py-2 rounded" :inputBorder="false"
					placeholder="账号" />
			</uni-forms-item>
			<uni-forms-item name="password">
				<uni-easyinput v-model="forms.password" class="input-bg-color py-2 rounded" :inputBorder="false"
					placeholder="密码" type="password" />
			</uni-forms-item>
			<uni-forms-item class="mt-3" name="gender" label="性别" labelAlign="center">
				<uni-data-checkbox v-model="forms.gender" :localdata="genderRange" mode="button" selectedColor="#ff584f" />
			</uni-forms-item>
			<button class="m-3">注册</button>
		</uni-forms>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				avatar: [],
				avatarStyle: {
					height: 120,
					width: 120,
					border: {
						width: "1px",
						style: "solid",
						radius: "8px"
					}
				},
				forms: {
					username: '',
					password: '',
					gender: 0
				},
				genderRange: [{
						value: 0,
						text: "未知",
					},
					{
						value: 1,
						text: "男",

					},
					{
						value: 2,
						text: "女",
					}
				],
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
			back() {
				uni.navigateBack({
					delta: 1
				})
			}
		}
	}
</script>

<style scoped>
	.avatar {
		width: 100%;
		height: 25vh;
	}

	.avatarSeat {
		height: 100%;
		width: 100%;
	}
</style>
