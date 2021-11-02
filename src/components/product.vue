<template>
	产品名：<input v-model="product.name"/><br>
	产品规格：<input v-model="product.specification"/><br>
	单位：<label v-for="(one) in gjh">
		<input type="radio" :value="one" v-model="product.company"/>{{one}}
	</label><br />
	生产日期：<input type="date" v-model="product.date"/><br />
	产品说明：<input v-model="product.description"/><br />
	产品分类：<label v-for="(two) in chy">
		<input type="radio" :value="two" v-model="product.classification"/>{{two}}
	</label><br>
	生产城市:
	<label v-for="(three) in sbtcz">
		<input type="checkbox" :value="three" v-model="product.city"/>{{three}}
	</label>
	<br>
</template>

<script>
	export default{
		data(){
			return{
				gjh:["个","件","盒"],
				chy:["吃","喝","用"],
				sbtcz:["上海","北京","天津","重庆","株洲"],
				product:{
					name:"",
					specification:"",
					company:"",
					date:"",
					description:"",
					classification:"",
					city:[]
				},
				products:[]
			}
		}
	}
</script>

<style>
</style>
