<template>
	<label>
		<input type="button" value="添加" @click="one($event)"/>
		<input type="button" value="删除" />
		<input type="button" value="删除所有" @click="threee()"/>
	</label><br>
	<label v-show="hidden">
		姓名：<input type="text" v-model="emp.name" /><br>
		<select v-model="emp.sex">
			<option value="男">男</option>
			<option value="女">女</option>
			<option value="未知">未知</option>
		</select><br>
		年龄：<input type="number" v-model="emp.age" />
		<br>
		<input type="button" value="确认添加" @click="four()"/>
	</label>
	
	<three ref="table"></three>
</template>
<script setup>
	import three from './components/Three.vue' 
</script>
<script>
	export default{
		data(){
			return{
				/* 是否隐藏填写用户信息 */
				hidden:false,
				// 当前用户
				emp:{
					id:1,
					name:"",
					sex:"",
					age:""
				},
				id:2
			}
		},
		methods:{
			one(event){
				/* 添加或者隐藏操作 */
				this.hidden=this.hidden?false:true
				this.hidden? event.target.value="隐藏" : event.target.value="添加"
			},
			threee(){
				//删除所有用户
				this.$refs.table.emps=[]
				//默认为不选
				this.$refs.table.hidden=false
				//清空ID
				this.$refs.table.check=[]
			},
			four(){
				//添加用户
				this.$refs.table.emps.push(this.emp)
				this.emp = {
					id:this.id,
					name:"",
					sex:"",
					age:""
				}
				//id自增
				this.id=this.id+1
			}
		}
	}
</script>
<style>

</style>
