<template>
	<view class="content">
		<!-- 
			平台区分 登录-->
		<!-- #ifdef MP-WEIXIN -->
		<button class="btn-auth" open-type="getUserInfo" @getuserinfo="wxGetUserInfo"
			withCredentials="true">微信授权获取用户信息</button>
		<!-- #endif -->
		<!-- #ifdef H5 || APP-PLUS-->
		<navigator url="/pages/login/login">
			<button class="btn-auth">登录</button>
		</navigator>
		<navigator url="/pages/login/mylogin">
			<button class="btn-auth">自己的登录界面</button>
		</navigator>
		<!-- #endif

 -->
		<!-- 
		<u-tabbar :value="tabvalue" @change="changeTab" :fixed="true" :placeholder="true" :safeAreaInsetBottom="true">
			<u-tabbar-item text="首页" icon="home" @click="changeTab"></u-tabbar-item>
			<u-tabbar-item text="放映厅" icon="photo" @click="changeTab"></u-tabbar-item>
			<u-tabbar-item text="直播" icon="play-right" @click="changeTab"></u-tabbar-item>
			<u-tabbar-item text="我的" icon="account" @click="changeTab"></u-tabbar-item>
		</u-tabbar> -->

	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabvalue: 0,
			}
		},
		onLoad() {

		},
		methods: {
			// 平台区分,登录
			wxGetUserInfo() {
				// #ifdef H5 || APP-PLUS
				uni.getStorage({
					key: 'userinfo',
					success: (res) => {
						this.auth = true;
						this.nickname = res.data.nickname;
						this.thumb = res.data.thumb;
					}
				})
				// #endif
			},
			// 切换标签页
			changeTab() {

			}

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
