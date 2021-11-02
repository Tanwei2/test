<template>
	<table border="1">
		<thead>
		<tr>
			<th style="min-width: 50px;"><input type="checkbox"/></th>
			<th style="min-width: 80px;">ID</th>
			<th style="min-width: 80px;">姓名</th>
			<th style="min-width: 80px;">性别</th>
			<th style="min-width: 80px;">年龄</th>
			<th style="min-width: 150px;"></th>
		</tr>
		</thead>
		<tbody>
		<tr v-for="(item) in emps">
			<td><input type="checkbox" :value="item.id"/></td>
			<td>{{item.id}}</td>
			<td>{{item.name}}</td>
			<td>{{item.sex}}</td>
			<td>{{item.age}}</td>
			<td>
				<input type="button" value="编辑"/>
				<input type="button" value="删除" @click="two(item.id)"/>
			</td>
		</tr>
		</tbody>
	</table>
</template>

<script>
	export default{
		data(){
			return{
				//所有用户
				emps:[],
				//判断是否被选中
				xuanzhong:false,
				/* 需要删除的用户下标 */
				check:[]
			}
		},
		methods:{
			two(index){
				/* 找到需要删除的用户ID的下标进行删除 */
				for (var i = 0; i < this.emps.length; i++) {
					if(index==this.emps[i].id){
						this.emps.splice(i,1)
					}
				}
			}
		}
	}
</script>

<style>
</style>
