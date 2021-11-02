<template>
	<div style="width: 200px; height: 50px; background-color: yellow; border: 1px solid #2C3E50;" v-bind:style="color">我是会变颜色的div</div>
	<input type="button" value="点我 变变变" v-on:click="one()"/>
</template>

<script>
	export default{
		data(){
		 return{
			color:''
		 }
		},
		methods:{
		 one(){
		  
		  var a=Math.floor((Math.random()*256));
		  var b=Math.floor((Math.random()*256));
		  var c=Math.floor((Math.random()*256));
		  this.color='background-color:#'+a+b+c;
		  console.log(a+'   '+b+'   '+c);
		 }
		}
	}
</script>

<style>
</style>
