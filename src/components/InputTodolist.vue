<template>
  <div>
    <input type="text"  v-model="text" :style="InputStyle" placeholder="enter your task here">
    <button  :onclick="add">Add as To-do</button>
    <button style="background-color: #e74c3c;" :onclick="removeTodo">remove</button>
  </div>
</template>

<script>
export default {
    name: "inputTodolist",
    props: ["list", "addTodo", "deleteTodo"],
    data(){
        return{
            text: '',
            InputStyle: {
                borderRadius: "3px",
                borderWidth: "2px",
                borderColor: "#7f8c8d",
                borderStyle: "solid",
                marginRight: "8px"
            }
        }
    },
    methods: {
      add(){
        this.text = this.addTodo(this.text);
      },
      removeTodo(){
        this.text = this.deleteTodo(this.text);
      }
    }
}
</script>

<style>

</style>