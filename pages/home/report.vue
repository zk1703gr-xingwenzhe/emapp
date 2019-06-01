<template>
	<view class="content">
		<view>
			<uni-list>
				<uni-list-item title="港口能耗对比" @click='fn(1)' 
					show-extra-icon="true" 
					:extra-icon="{color: '#4cd964',size: '22',type: 'list'}"  >
				</uni-list-item>
				<uni-list-item title="流程作业量对比" @click='fn(2)' 
					show-extra-icon="true" 
					:extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"  >
				</uni-list-item>
				<uni-list-item title="成本核算信息" @click='fn(3)' 
					show-extra-icon="true" 
					:extra-icon="{color: '#4cd964',size: '22',type: 'spinner'}"  >
				</uni-list-item>
			</uni-list>
		</view>
	</view>
</template>

<script>
	import uniList from '@dcloudio/uni-ui/lib/uni-list/uni-list.vue'
	import uniListItem from '@dcloudio/uni-ui/lib/uni-list-item/uni-list-item.vue'
	export default {
		components:{uniList,uniListItem},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			fn(index){
				if(index==3){
					uni.navigateTo({
						url:"../tables/table02"
					})
				}else if(index==1){
					uni.navigateTo({
						url:"../charts/chart03"
					})
				}else if(index==2){
					uni.navigateTo({
						url:"../charts/chart04"
					})
				}
			}
		}
	}
</script>

<style>
	page{
		background: #F4F4F4;
	}
</style>
