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
				data2:[],
				data3:[]
	        }
	    },
		onLoad:function () {
			var compid;
			uni.getStorage({
				key: 'baseUser',
				success:  (res)=> {
					compid = res.data.compid;
					// 与后端进行交互
					uni.request({
						url: this.url+"jobAmount/flowAmount?year=2019&compid="+compid,
						data: {
						},
						header: {
							'custom-header': 'hello' //自定义请求头信息
						},
						success: (res) => {
							console.log(res.data);
							// data1
							for(var i=1;i<res.data.columns.length;i++){
								this.data1.push(res.data.columns[i]);
							}
							// data2
							for(var i=0;i<res.data.rows.length;i++){
								this.data2.push(res.data.rows[i].月份);
							}
							// data3
							for(var obj of this.data1){
								var arr = [];
								for(var i=0;i<res.data.rows.length;i++){
									
									arr.push(res.data.rows[i][obj]);
								}
								this.data3.push({
											name:obj,
											type:'line',
											stack: '总量',
											data:arr
										});
							}
							
						}
					});
				}
			});
			
			
		},
		methods: {
			
			lineInit(canvas, width, height) {
				console.log(this.data1);
				console.log(this.data2);
				console.log(this.data3);
				lineChart = echarts.init(canvas, null, {
					width: width,
					height: height
				})
				canvas.setChart(lineChart)
				var option = {
					title: {
						text: '流程作业量对比图'
					},
					tooltip: {
						trigger: 'axis'
					},
					legend: {
						data:this.data1
					},
					grid: {
						left: '3%',
						right: '4%',
						bottom: '3%',
						containLabel: true
					},
					toolbox: {
						feature: {
							saveAsImage: {}
						}
					},
					xAxis: {
						type: 'category',
						boundaryGap: false,
						data: this.data2
					},
					yAxis: {
						type: 'value'
					},
					series: this.data3
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
