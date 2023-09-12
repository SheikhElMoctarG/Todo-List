<template>
  <div>
    <h1>ToDo list app</h1>
    <input-todolist :addTodo="addTodo" :list="list" :deleteTodo="deleteTodo"/>
    <div v-for="item of list" :key="item">
      <todo-card :title="item"/>
    </div>
    <div class="footer">
      if want to remove a task, you should enter the value of it in that input.
    </div>
  </div>
</template>

<script>
import InputTodolist from './components/InputTodolist.vue'
import TodoCard from './components/TodoCard.vue'

export default {
  name: 'App',
  data(){
    return {
      list: []
    }
  },
  components: {
    TodoCard,
    InputTodolist
  },
  created(){
    this.list = this.getList();
    this.updateList();
  },
  methods: {
    getList(){
      return JSON.parse(localStorage.getItem('list')) || [];
    },
    updateList(){
      return localStorage.setItem('list', JSON.stringify(this.list));
    },
    addTodo(item){
      // console.log("this is a value: " + item);
      // console.log("this is a result: " + (item.length).toString())
      if(item.length != 0){
        this.list.push(item);
        this.updateList();
      } 
      return '';
    },
    deleteTodo(item){
      if(item.length != 0){
        const indexOfelement = this.getIdByValue(item);
        if(indexOfelement != undefined){
          this.list.splice(indexOfelement, indexOfelement);
          this.updateList();
        }
      } 
      return item;
    },
    getIdByValue(value){
      for (let i = 0; i < this.list.length; i++) {
        if(this.list[i] == value){
          return i;
        }
      }
      return undefined;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
    background-color: green;
    color: #eee;
    padding: 5px;
    border: 0px solid green;
    border-radius: 6px;
    font-size: 15px;
    font-family: cursive;
    margin: 2px;
}
</style>
