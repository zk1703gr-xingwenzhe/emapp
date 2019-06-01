<template>
	<view class="content">
		<view>
			<wuc-tab :tab-list="tabList" :tabCur.sync="TabCur" @change="tabChange" textFlex='true'></wuc-tab>
			<view v-if="TabCur==0">
				<synchro></synchro>
			</view>
			<view v-else-if="TabCur==1">
				<phones></phones>
			</view>
			<view v-else>
				故障记录组件
			</view>
		</view>
	</view>
</template>

<script>
	import WucTab from '@/components/wuc-tab/wuc-tab.vue'
	import synchro from '../yw/synchro.vue'
	import phones from '../home/phones.vue'
	export default {
		components: {WucTab,synchro,phones},
		data() {
			return {
			  TabCur: 0,
			  tabList: [{ name: '数据采集' }, { name: '通讯录' }, { name: '故障记录' }],
			}},
		methods: {
			tabChange(index) {
				this.TabCur = index;
			}
		}
	}
</script>

<style>
	@import url("../../static/css/yw.css");	
</style>
