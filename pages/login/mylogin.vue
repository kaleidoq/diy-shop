<template>
	<view class="login">
		<view class="user-icon">
			<image :src="userImg"></image>
		</view>
		<u-form labelPosition="left" :model="loginInfo" :rules="loginRules" :errorType="errorType" ref="loginForm">
			<u-form-item label="姓名" labelWidth="50px" prop="username" borderBottom>
				<u--input v-model="loginInfo.username" border="none" clearable />
			</u-form-item>
			<u-form-item label="姓名" labelWidth="50px" prop="password" borderBottom>
				<!-- <u--input v-model="loginInfo.password" border="none" clearable/> -->

			</u-form-item>
		</u-form>
		<!-- 登录按钮 -->
		<view class="btn">
			<u-button size="default" :loading="isLogining" :ripple="true" @click="login">
				{{ isLogining ? "" : "登 录" }}
			</u-button>
		</view>
		<u-toast ref="uToast"></u-toast>
		<view class="copy-right">标签</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				loginInfo: {
					username: "",
					password: "",
				},
				// 登录界面的用户图标
				userImg: "../../static/icon/icon-1/user.png",
				// 登录按钮的懒加载
				isLogining: false,
				// 输入框的长度
				pdMaxLength: 100,
				loginRules: {
					username: [{
						required: true,
						message: '请输入姓名',
						trigger: ['blur', 'change']
					}]
				},
				// 验证错误消息提示
				errorType: 'border-bottom',
				isFocus: false,
				focus: false
			};
		},
		methods: {
			// userFocus() {
			// 	// 是否在焦点上
			// 	this.isFocus = true
			// },
			// userBlur() {
			// 	setTimeout(() => {
			// 		this.isFocus = false
			// 	}, 1)
			// },

			focus() {
				this.isFocus = true
			},
			blur() {
				// 失去焦点事件先于清除事件触发，因此让其延迟即可先触发 clearInput 事件
				setTimeout(() => {
					this.isFocus = false
				}, 1)
			},

			// 登录按钮
			login() {},
		},
	};
</script>

<style lang="scss" scoped>
	.login {
		width: 80%;
		margin: auto;
	}

	.user-icon {
		margin-top: 200rpx;
		margin-bottom: 50rpx;
		width: 100%;
		display: flex;
		justify-content: center;

		>image {
			width: 150rpx;
			height: 150rpx;
		}
	}

	.btn {
		margin-top: 40rpx;

		.login-btn {
			width: 100%;
			border-radius: 20rpx;
			border: $uni-color-primary;
			background-color: $uni-color-primary;
			color: $uni-text-color-inverse;
		}
	}

	.copy-right {
		// bottom: 100rpx;
		bottom: 0;
		width: 100%;
		color: $uni-text-color-grey;
		text-align: center;
		font-size: 24rpx;
	}
</style>
