<template>
	<child ref="product"></child>
	<input type="button" value="加入列表" @click="one()"/>
	<input type="button" value="打印" @click="two()" />
	
	<table border="1" v-show="hidd">
		<thead>
		<tr>
			<th>产品名</th>
			<th>产品规格</th>
			<th>单位</th>
			<th>生产日期</th>
			<th>产品说明</th>
			<th>产品分类</th>
			<th>生产城市</th>
		</tr>
		</thead>
		<tbody>
		<tr v-for="(item) in msg">
			<td>{{item.name}}</td>
			<td>{{item.specification}}</td>
			<td>{{item.company}}</td>
			<td>{{item.date}}</td>
			<td>{{item.description}}</td>
			<td>{{item.classification}}</td>
			<td>{{item.city}}</td>
		</tr>
		</tbody>
	</table>

</template>

<script setup>
import child from "./components/product.vue"
</script>
<script>
	export default{
		data(){
			return{
				msg:[],
				hidd:false
			}
		},
		methods:{
			one(){
				this.$refs.product.products.push(this.$refs.product.product)
				this.$refs.product.product={
					name:"",
					specification:"",
					company:"",
					date:"",
					description:"",
					classification:[],
					city:[]
				}
				this.hidd=false
			},
			two(){
				this.hidd=true
				this.msg=this.$refs.product.products
			}
		}
	}
</script>
