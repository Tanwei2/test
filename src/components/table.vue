<template>
	<table border="1">
		<thead>
			<tr>
				<th style="min-width: 50px;">
					<input type="checkbox" @click="there($event)" :checked="hidden" />
				</th>
				<th style="min-width: 80px;">ID</th>
				<th style="min-width: 80px;">姓名</th>
				<th style="min-width: 80px;">性别</th>
				<th style="min-width: 80px;">年龄</th>
				<th style="min-width: 150px;"></th>
			</tr>
		</thead>
		<tbody>
			<tr v-for="(item,index) in emps">
				<td>
					<input type="checkbox" :value="item.id" v-model="check" @change="fix()" />
				</td>
				<td>{{ item.id }}</td>
				<td>{{ item.name }}</td>
				<td>{{ item.sex }}</td>
				<td>{{ item.age }}</td>
				<td>
					<input type="button" value="编辑" @click="one(item.id)" />
					<input type="button" value="删除" @click="two(item.id)" />
				</td>
			</tr>
		</tbody>
	</table>
</template>

<script>
export default {
	data() {
		return {
			/* 所有的用户 */
			emps: [],
			/* 当前需要编辑的下标 */
			update: 0,
			/* 需要删除的用户下标 */
			check: [],
			/* 判断全选是否被选中 */
			hidden: false,

		}
	},
	methods: {
		/* 编辑操作 */
		one(index) {
			/* 通过需要修改的用户对象给用户对象赋值 */
			for (var i = 0; i < this.emps.length; i++) {
				if (index == this.emps[i].id) {
					this.$parent.emp.id = this.emps[i].id
					this.$parent.emp.name = this.emps[i].name
					this.$parent.emp.sex = this.emps[i].sex
					this.$parent.emp.age = this.emps[i].age
					this.$parent.$refs.button.value = "确认编辑"
					this.update = i
				}
			}
		},
		/* 删除单个操作 */
		two(index) {
			/* 找到需要删除的用户ID的下标进行删除 */
			for (var i = 0; i < this.emps.length; i++) {
				if (index == this.emps[i].id) {
					this.emps.splice(i, 1)
				}
			}
		},
		/* 全选操作 */
		there(event) {
			/* 先清空所有需要删除的用户ID */
			this.check = []
			if (event.target.checked) {
				/* 添加所有的用户ID */
				for (var i = 0; i < this.emps.length; i++) {
					this.check.push(this.emps[i].id)
				}
				/* 设置全选为选中状态 */
				this.hidden = true
			} else {
				/* 清空所有需要删除的用户ID*/
				this.check = []
				/* 设置全选为未选中状态 */
				this.hidden = false
			}
		},
		/* 单选操作 */
		fix() {
			/* 判断是否全选 */
			if (this.emps.length == this.check.length) {
				this.hidden = true
			} else {
				this.hidden = false
			}
		}
	}
}
</script>

<style>
th {
	text-align: center;
}

td {
	text-align: center;
}
</style>
