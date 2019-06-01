<template>
	<view class="content">
		<view class="buttons">
			<button @click="fn">数据采集</button>
		</view>
		<view class="day">
			今天同步了{{arr.length}}次
		</view>
		<view>
			同步记录
		</view>
		<view>
			<uni-badge v-for="obj in arr" :text="obj" type="success"></uni-badge>
		</view>
	</view>
</template>

<script>
	import uniBadge from "@dcloudio/uni-ui/lib/uni-badge/uni-badge.vue"
	export default {
		components: {uniBadge},
		data() {
			return {
				title:'Hello',
				arr:[]
			}
		},
		onLoad() {
			uni.getStorage({
				key:"synchro",
				success: (res)=>{
					this.arr = res.data;
				}
			})
		},
		methods:{
			fn(){
				var date = new Date();
				var ctime = date.getHours()+':'+date.getMinutes();
				this.arr.push('同步时间'+ctime);
				uni.setStorage({
					key:'synchro',
					data:this.arr
				})
				// 获取compid
				uni.getStorage({
					key:'baseUser',
					success:(res)=>{
						var compid = res.data.compid;
						// 向后端发送请求
						uni.request({
							url: this.url+ 'produceReport/initCurrentDay?compid='+compid, //仅为示例，并非真实接口地址。
							data: {
								
							},
							header: {
								'custom-header': 'hello' //自定义请求头信息
							},
							success: (res) => {
								uni.showToast({
									title:"采集成功"
							})
						}
					});
				}
			});
		}
	}
}
</script>

<style>
	.content {
		text-align: center;
		height: 400upx;
	}

	.logo {
		height: 200upx;
		width: 200upx;
		margin-top: 200upx;
	}

	.title {
		font-size: 36upx;
		color: #8f8f94;
	}
</style>
