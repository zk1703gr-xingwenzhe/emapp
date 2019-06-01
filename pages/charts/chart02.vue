<template>
	<view class="body" scroll-y="true" >
		<!-- 注意：class="chart-father" 必不可少，否则图表显示不出来 -->
		<view class="chart-father">
			<mpvue-echarts :echarts="echarts" :onInit="lineInit" canvasId="line"  />
		</view>
	</view>
</template>

<script>
	import * as echarts from '../../components/demo-echart/echarts/echarts.simple.min.js';
	import mpvueEcharts from '../../components/demo-echart/mpvue-echarts/src/echarts.vue';
	var lineChart=null;
	
	
	export default {
	    data() {
	        return {
				echarts: echarts
	        }
	    },
		onLoad:function (option) {
			console.log(option.flowname);
		},
		methods: {
			
			lineInit(canvas, width, height) {
				lineChart = echarts.init(canvas, null, {
					width: width,
					height: height
				})
				canvas.setChart(lineChart)
				var option = {
					title : {
						text: '某站点用户访问来源',
						subtext: '纯属虚构',
						x:'center'
					},
					tooltip : {
						trigger: 'item',
						formatter: "{a} <br/>{b} : {c} ({d}%)"
					},
					legend: {
						orient: 'vertical',
						left: 'left',
						data: ['斗轮机','装船机','皮带机']
					},
					series : [
						{
							name: '访问来源',
							type: 'pie',
							radius : '55%',
							center: ['50%', '60%'],
							data:[
								{value:535, name:'斗轮机'},
								{value:310, name:'装船机'},
								{value:234, name:'皮带机'}
								
							],
							itemStyle: {
								emphasis: {
									shadowBlur: 10,
									shadowOffsetX: 0,
									shadowColor: 'rgba(0, 0, 0, 0.5)'
								}
							}
						}
					]
				};
				lineChart.setOption(option)
				return lineChart
			}
			
			
		},
		components: {
			mpvueEcharts
		},
		
	}
</script>

<style>
	.chart-father{
		display: flex;
		margin-top: -10upx;
		width: 100%;
		height: 500upx;
		background: #F4F4F4;
		justify-content: center;
	}
	
</style>
