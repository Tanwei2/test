<template>
			你喜欢的城市是？
			<button type="button" @click="a">全选</button>
			<button type="button" @click="b">全不选</button>
			<button type="button" @click="c">反选</button>

			<input type="checkbox" value="长沙" v-model="v" />长沙
			<input type="checkbox" value="上海" v-model="v" />上海
			<input type="checkbox" value="广州" v-model="v" />广州
			<br>
			您选择了：{{v}}
</template>

<script>
export default{
	data() {
		return {
			v: []
		}
	},
	methods: {
		a: function() {
			this.v.push('长沙')
			this.v.push('上海')
			this.v.push('广州')
		},
		b: function() {
			this.v = []
		},
		c: function() {
			var nv = ['长沙', '上海', '广州']
			this.v.forEach(function(e) {
				var index = nv.indexOf(e);
				nv.splice(index, 1)
			})
			this.v = nv
	
		}
	}
}

</script>
