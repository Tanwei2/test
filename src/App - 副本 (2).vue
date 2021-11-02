<template>
  <input type="button" value="添加" @click="one($event)" />
  <input type="button" value="删除" @click="two()" />
  <input type="button" value="删除所有" @click="there()" />
  <br />
  <label v-show="hidden">
    姓名：<input type="text" v-model="emp.name" /><br />
    性别：
    <select v-model="emp.sex">
      <option value="男">男</option>
      <option value="女">女</option>
      <option value="未知">未知</option></select
    ><br />
    年龄：<input type="number" v-model="emp.age" /><br />
    <input type="button" value="确认添加" @click="four($event)" ref="button" />
  </label>
  <tables ref="table"></tables><br />
</template>
<script setup>
import tables from "./components/table.vue";
</script>
<script>
export default {
  data() {
    return {
      /* 是否隐藏填写用户信息 */
      hidden: false,
      /* ID自增 */
      id: 2,
      /* 当前用户 */
      emp: {
        id: 1,
        name: "",
        sex: "",
        age: "",
      },
    };
  },
  methods: {
    /* 添加或者隐藏操作 */
    one(event) {
      this.hidden = this.hidden ? false : true;
      this.hidden
        ? (event.target.value = "隐藏")
        : (event.target.value = "添加");
    },
    /* 删除操作 */
    two() {
      /* 删除全部 */
      if (this.$refs.table.hidden) {
        /* 清空所有的用户 */
        this.$refs.table.emps = [];
        /* 设置全选为未选中状态 */
        this.$refs.table.hidden = false;
      } else {
        /* 迭代找到需要删除的用户进行删除 */
        for (var x = 0; x < this.$refs.table.check.length; x++) {
          for (var y = 0; y < this.$refs.table.emps.length; y++) {
            if (this.$refs.table.check[x] == this.$refs.table.emps[y].id) {
              this.$refs.table.emps.splice(y, 1);
            }
          }
        }
        /* 清空需要删除的用户ID */
        this.$refs.table.check = [];
      }
    },
    /* 删除所有操作 */
    there() {
      /* 清空所有的用户 */
      this.$refs.table.emps = [];
      /* 设置全选为未选中状态 */
      this.$refs.table.hidden = false;
      /* 清空需要删除的用户ID */
      this.$refs.table.check = [];
    },
    /* 确认添加操作 */
    four(event) {
      if (event.target.value == "确认编辑") {
        /* 修改按钮值 */
        event.target.value = "确认添加";
        /* 找到需要修改的用户ID进行修改 */
        this.$refs.table.emps.splice(this.$refs.table.update, 1, this.emp);
        /* 初始化用户对象 */
        this.emp = {
          id: this.id,
          name: "",
          sex: "",
          age: "",
        };
      } else {
        /* 将用户对象添加到用户列表中 */
        this.$refs.table.emps.push(this.emp);
        /* 初始化用户对象 */
        this.emp = {
          id: this.id,
          name: "",
          sex: "",
          age: "",
        };
        /* 自增ID */
        this.id = this.id + 1;
        /* 设置全选为未选中状态 */
        this.$refs.table.hidden = false;
      }
    },
  },
};
</script>
<style></style>
