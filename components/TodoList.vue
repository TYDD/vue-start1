<template>
    <div class="hello">
      <header>TODO</header>
      <input
        type="text"
        placeholder="请填入今日任务吧"
        v-on:input="inputitem"
        v-model="text" />
      <button @click="addItem1" class="additem">增加</button>
      <ul class="todo-list" v-show="lists.length">
        <li
          class="todo-item"
          v-for="(item, index) in this.lists"
          v-bind:key="item">
          <span>{{ index + 1 }}</span>
          <p>{{ item }}</p>
          <button @click="removeItem(index)">完成</button>
        </li>
      </ul>
      <div class="todo-nodata" v-show="!lists.length">
        请及时添加任务，开始今天的学习吧！
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "HelloWorld",
    props:{
      todoList: Array
    },
    data() {
      return {
        text: "",
        lists: [],
      }
    },
    methods: {
      addItem1() {
        if (this.text === "") alert("请输入任务")
        else {
          this.lists.push(this.text)
          this.text = ""
        }
      },
      inputitem(e) {
        // console.log(e.target.value)
        this.text = e.target.value
      },
      removeItem(index) {
        //删除index,一位
        this.lists.splice(index, 1)
      },
    },
    beforeCreate() {
      console.log(this.lists)
    },
    created(){
      this.lists = this.todoList
    },
   
  }
  </script>
  <style scoped>
  header {
    font-size: 28px;
    line-height: 40px;
    text-align: center;
  }
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }
  .hello {
    width: 400px;
    height: 500px;
    margin: 80px auto;
  }
  input {
    height: 34px;
    margin-right: 20px;
    padding-left: 10px;
    border: 1px solid #ccc;
    border-radius: 6px;
    margin-bottom: 20px;
  }
  .additem {
    width: 70px;
    height: 36px;
    background-color: #409eff;
    border: none;
    border-radius: 6px;
    color: #fff;
  }
  .todo-item {
    display: flex;
    padding: 0 20px;
    height: 40px;
  }
  .todo-item span {
    padding-right: 10px;
  }
  .todo-item p {
    flex: 1;
    margin-top: 0px;
  }
  .todo-item button {
    width: 50px;
    height: 28px;
    background-color: red;
    border: none;
    border-radius: 6px;
    color: #fff;
  }
  .todo-nodata {
    font-size: 18px;
    line-height: 80px;
    text-align: center;
    color: #409eff;
  }
  </style>