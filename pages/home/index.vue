<template>
	<view>
		<uni-notice-bar show-close="true" speed="50" show-icon="true" scrollable="true" single="true" :text="text"></uni-notice-bar>
		<uni-segmented-control :current="current" :values="items" @clickItem="onClickItem" style-type="text" active-color="#1296db"></uni-segmented-control>
		<view v-show="current === 0">
			<energy></energy>
		</view>
		<view v-show="current === 1">
			<produce></produce>
		</view>
		<view v-show="current === 2">
			<rank></rank>
		</view>
	</view>
</template>

<script>
	import uniNoticeBar from "@dcloudio/uni-ui/lib/uni-notice-bar/uni-notice-bar.vue"
	import uniSegmentedControl from "@dcloudio/uni-ui/lib/uni-segmented-control/uni-segmented-control.vue"
	import energy from "../index/energy.vue"
	import produce from "../index/produce.vue"
	import rank from "../index/rank.vue"
	export default {
		components: {
			uniNoticeBar,
			uniSegmentedControl,
			energy,
			produce,
			rank
		},
		data() {
			return {
				items: ['能耗', '产销', '排名'],
				current: 0,
				text:'通知：本系统正在开发中，欢迎大家及时在我的专栏反馈信息页面提供建议，如有疑问请联系管理员，QQ号1967609601，如有建议请及时反馈，感激不尽！！！'
			}
		},
		methods: {
			onClickItem(index) {
				this.current = index;
			}
		}
	}
</script>

<style>
	@import url("../../static/css/index.css");
</style>
