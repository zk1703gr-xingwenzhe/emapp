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
				echarts: echarts,
				data1:[],
				data2:[]
	        }
	    },
		onLoad:function () {
			console.log(1);
			uni.request({
					url: this.url + 'devInfo/consume?year=2018',
					data: {
					},
					header: {
						'custom-header': 'login'
					},
					success: (res) => {
						var arr = res.data.rows;
						for(var obj of arr){
							this.data1.push(obj.港口名称);
							this.data2.push({value:obj.皮带机+obj.斗轮机+obj.装船机,name:obj.港口名称})
						}
						
					}
				})
		},
		methods: {
			
			lineInit(canvas, width, height) {
				console.log(2);
				console.log(this.data1);
				console.log(this.data2);
				lineChart = echarts.init(canvas, null, {
					width: width,
					height: height
				})
				canvas.setChart(lineChart)
				var option = {
					title : {
						text: '港口能耗对比图',
						subtext: '能耗对比',
						x:'center'
					},
					tooltip : {
						trigger: 'item',
						formatter: "{a} <br/>{b} : {c} ({d}%)"
					},
					legend: {
						orient: 'vertical',
						left: 'left',
						data: this.data1
					},
					series : [
						{
							name: '访问来源',
							type: 'pie',
							radius : '55%',
							center: ['50%', '60%'],
							data:this.data2,
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
