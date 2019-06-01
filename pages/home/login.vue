<template>
	<view class="content">
		<input type="text" focus v-model="username" placeholder="请输入用户名"></input>
		<view>
			<input type="password"  v-model="password" placeholder="请输入密码"></input>
			<uni-icon type="eye" size="20" @click='flagEye'></uni-icon>
		</view>
		<button type="primary" @click="login">登录</button>
	</view>
</template>

<script>
	import uniIcon from "@dcloudio/uni-ui/lib/uni-icon/uni-icon.vue"
	export default {
		components: {
			uniIcon
		},
		data() {
			return {
				username: "lhx",
				password: "123456",
				flag: true
			}
		},
		methods: {
			flagEye() {
				this.flag=!this.flag;
			},
			login() {
				//登录条件
				if (this.username.length <= 0) {
					uni.showToast({
						icon: 'none',
						title: '请输入用户名',
						duration: 1000
					});
					return;
				}
				if (this.password.length <= 0) {
					uni.showToast({
						icon: 'none',
						title: '请输入密码',
						duration: 1000
					});
					return;
				}
				//网络请求
				uni.request({
					url: this.url + 'baseUser/login',
					data: {
						username: this.username,
						password: this.password
					},
					header: {
						'custom-header': 'login'
					},
					success: (res) => {
						if ((this.username != res.data.username) && (this.password != res.data.password)) {
							uni.showToast({
								icon: 'none',
								title: '用户名或密码不正确',
								duration: 1000
							});
						} else {
							uni.setStorage({
								key: 'baseUser',
								data: res.data
							});
							uni.switchTab({
								url: 'index'
							});
							uni.showToast({
								icon: 'success',
								title: '登录成功',
								duration: 1000
							});
						}
					},
					fail: () => {
						uni.showToast({
							icon: 'none',
							title: '网络异常,请稍后重试',
							duration: 1000
						});
					}
				})
			}
		},
		onNavigationBarButtonTap() {
			uni.navigateTo({
				url: 'register'
			});
		}
	}
</script>

<style>
	@import url("../../static/css/login.css");
</style>
