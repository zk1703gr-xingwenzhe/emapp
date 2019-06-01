<template>
	<view class="wrap">
		<view class="div-table">
			<view class="thead">
				<view class="th">
					<view class="td">排名</view>
					<view class="td">港口名称</view>
					<view class="td">能耗率</view>
				</view>
			</view>
			<view class="tr">
				<view class="td">1</view>
				<view class="td">周口港</view>
				<view class="td">63</view>
			</view>
			<view class="tr">
				<view class="td">2</view>
				<view class="td">上海港</view>
				<view class="td">53</view>
			</view>
			<view class="tr">
				<view class="td">3</view>
				<view class="td">漯河港</view>
				<view class="td">44</view>
			</view>
			<view class="tr">
				<view class="td">4</view>
				<view class="td">日照港</view>
				<view class="td">21</view>
			</view>
			
		</view>
		
	</view>
</template>

<script>
export default {
	data() {
		return {};
	}
};
</script>

<style lang="scss">
.h1 {
	text-align: left;
	font-size: 30upx;
	font-weight: bold;
	padding: 10upx 0;
}
.wrap {
	margin: 20upx;
}
$div-table-border-color: #666;
$div-table-border-width: 1upx;

.div-table {
	display: table;
	width: 100%;
	height: 100%;
	border: $div-table-border-width solid $div-table-border-color;
	box-sizing: border-box;
	table-layout: fixed;
	position: relative;
	.celspan {
		display: table;
		width: 100%;
		height: 100%;
		.td {
			display: table-cell;
			border: none !important;
		}
		.td + .td {
			border-left: $div-table-border-width solid $div-table-border-color !important;
		}
	}
	.rowspan {
		display: table;
		width: 100%;
		height: 100%;
		.tr {
			display: table-row;
			border: none !important;
		}
	}

	&.fixed-thead {
		.tbody,
		.thead,
		.tr,
		.th,
		.td {
			display: block;
		}
		.tr,
		.th {
			&:after {
				content: '';
				display: block;
				visibility: hidden;
				clear: both;
				height: 0;
			}
		}
		.td {
			float: left;
			width: 33.33%;
		}
		.tbody {
			height: 400upx;
			overflow-y: auto;
			overflow-x: hidden;
		}
	}

	.tr,
	.th {
		display: table-row;
		& + .tr,
		& + .th {
			.td,
			.th {
				border-top: $div-table-border-width solid $div-table-border-color;
				word-break: break-word;
			}
		}
	}
	.rowspan {
		.tr,
		.th {
			display: table-row;
			.td,
			.th {
				border: none;
			}
			& + .tr,
			& + .th {
				.td,
				.th {
					border-top: $div-table-border-width solid $div-table-border-color;
				}
			}
		}
	}
	.td {
		display: table-cell;
		vertical-align: middle;
		text-align: center;
		box-sizing: border-box;
		padding: 10upx;
		&.noPadding {
			padding: 0;
		}
		& + .td {
			border-left: $div-table-border-width solid $div-table-border-color;
		}
	}
	.th .td {
		font-weight: bold;
	}
	.tbody {
		display: table-row-group;
	}
	.thead {
		display: table-header-group;
		.tr,
		.th {
			.td,
			.th {
				border-bottom: $div-table-border-width solid $div-table-border-color;
			}
		}
	}
	.tfoot {
		display: table-footer-group;
		.tr,
		.th {
			.td,
			.th {
				border-top: $div-table-border-width solid $div-table-border-color;
			}
		}
	}
	.colgroup {
		display: table-column-group;
	}
	.col {
		display: table-column;
	}
	.caption {
		display: table-caption;
	}
}
</style>
