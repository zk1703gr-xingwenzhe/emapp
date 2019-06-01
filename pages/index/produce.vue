<template>
	<view>
		<!-- 环形 -->
		<view class="produce">
			<view class="circle">
				<view class="font1">29<label class="text1">天</label></view>
				<label class="label">安全用机</label><br>
				<label class="label">/</label>
				<view class="font2">10<label class="text1">条</label></view>
				<label class="label">异常设备</label>
			</view>
		</view>
		<view class="fuhao">~</view>
		<view class="text2">作业量统计</view>
		<view class="text3">☰</view>
		<!-- 列表 -->
		<uni-list>
			<uni-list-item title="流程fm1" @click='fn("流程fm1")' show-extra-icon="true"
			 :extra-icon="{color: '#4cd964',size: '22',type: 'flag'}"
			 show-badge="true" badge-text="130.5"></uni-list-item>
			 
			<uni-list-item title="流程fm2" @click='fn("流程fm2")' show-extra-icon="true" 
			 :extra-icon="{color: '#4cd964',size: '22',type: 'flag'}"
			 show-badge="true" badge-text="1230.6"></uni-list-item>
			 
			<uni-list-item title="流程fm3" @click='fn("流程fm3")' show-extra-icon="true"
			 :extra-icon="{color: '#4cd964',size: '22',type: 'flag'}"
			 show-badge="true" badge-text="801.6"></uni-list-item>
			 
			<uni-list-item title="流程fm4" @click='fn("流程fm4")' show-extra-icon="true"
			 :extra-icon="{color: '#4cd964',size: '22',type: 'flag'}"
			 show-badge="true" badge-text="81.6"></uni-list-item>
			 
			<uni-list-item title="流程fm5" @click='fn("流程fm5")' show-extra-icon="true"
			 :extra-icon="{color: '#4cd964',size: '22',type: 'flag'}"
			 show-badge="true" badge-text="52.7"></uni-list-item>
			 
			<uni-list-item title="流程fm6" @click='fn("流程fm6")' show-extra-icon="true"
			 :extra-icon="{color: '#4cd964',size: '22',type: 'flag'}"
			 show-badge="true" badge-text="52.7"></uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	import uniList from '@dcloudio/uni-ui/lib/uni-list/uni-list.vue'
	import uniListItem from '@dcloudio/uni-ui/lib/uni-list-item/uni-list-item.vue'
	export default {
		components: {
			uniList,
			uniListItem
		},
		data() {
			return {}
		},
		methods: {
			fn(flowname) {
				uni.navigateTo({
					url: "../charts/chart02"
				});
			}
		}
	}
</script>

<style>

</style>