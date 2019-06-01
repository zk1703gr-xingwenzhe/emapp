<template>
	<view class="content">
		<view>
			<text class="title">港口能耗排名</text>
			<table01></table01>
		</view>
	</view>
</template>

<script>
	import table01 from "../tables/table01.vue"
	export default {
		components: {
			table01
		},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

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
