<template>
	<view>
		<phone-directory :phones="phones" @paramClick="paramClick"></phone-directory>
	</view>
</template>

<script>
	import phoneDirectory from '@/components/phone-directory/phone-directory.vue'
	export default {
		name:"phones",
		components:{
			phoneDirectory
		},
		data() {
			return {
				//示例数据
				phones:{
					 "A": [{
                        "id": 56,
                        "spell": "aba",
                        "name": "阿坝"
                    }, {
                        "id": 57,
                        "spell": "akesu",
                        "name": "阿克苏"
                    }, {
                        "id": 58,
                        "spell": "alashanmeng",
                        "name": "阿拉善盟"
                    }, {
                        "id": 59,
                        "spell": "aletai",
                        "name": "阿勒泰"
                    }, {
                        "id": 60,
                        "spell": "ali",
                        "name": "阿里"
                    }, {
                        "id": 61,
                        "spell": "ankang",
                        "name": "安康"
                    }, {
                        "id": 62,
                        "spell": "anqing",
                        "name": "安庆"
                    }, {
                        "id": 63,
                        "spell": "anshan",
                        "name": "鞍山"
                    }, {
                        "id": 64,
                        "spell": "anshun",
                        "name": "安顺"
                    }, {
                        "id": 65,
                        "spell": "anyang",
                        "name": "安阳"
                    }, {
                        "id": 338,
                        "spell": "acheng",
                        "name": "阿城"
                    }, {
                        "id": 339,
                        "spell": "anfu",
                        "name": "安福"
                    }, {
                        "id": 340,
                        "spell": "anji",
                        "name": "安吉"
                    }, {
                        "id": 341,
                        "spell": "anning",
                        "name": "安宁"
                    }, {
                        "id": 342,
                        "spell": "anqiu",
                        "name": "安丘"
                    }, {
                        "id": 343,
                        "spell": "anxi",
                        "name": "安溪"
                    }, {
                        "id": 344,
                        "spell": "anyi",
                        "name": "安义"
                    }, {
                        "id": 345,
                        "spell": "anyuan",
                        "name": "安远"
                    }],
                    "B": [{
                        "id": 1,
                        "spell": "beijing",
                        "name": "北京"
                    }, {
                        "id": 66,
                        "spell": "baicheng",
                        "name": "白城"
                    }, {
                        "id": 67,
                        "spell": "baise",
                        "name": "百色"
                    }, {
                        "id": 68,
                        "spell": "baishan",
                        "name": "白山"
                    }]
				}
			}
		},
		methods : {
			paramClick (e) {
				console.log(e)
			}
		}
	}
</script>

<style>

</style>
