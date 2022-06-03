<script>
export default {
  name: 'app',
  data() {
    return {
      newTodo: '',
      todos: [
        {
          id: 1,
          text: 'Learn Vue',
          completed: false
        },
        {
          id: 2,
          text: 'Complete Vue Project',
          completed: false
        },
        {
          id: 3,
          text: 'Take a break',
          completed: false
        }
      ]
    }
  },
methods: {
  addTodo() {
    this.todos.push({
      id: this.todos.length + 1,
      text: this.newTodo,
      completed: false
    })
    this.newTodo = ''
  },
  deleteTodo(i){
    this.todos.splice(i,1)
  }
}}
</script>

<template>
  <div id="app">
    <div id="container">

      <h1>June Todo List:</h1>
    <input type="text" class="input" placeholder="Add New Task" v-model="newTodo" />
    <button class="add-button" v-on:click="addTodo()"  @click.enter="newTodo">Submit</button>
   <!-- <div v-for="todo in todos" :key="todo-list"> -->
<ul>
       <li v-for="(todo,i) in todos">
       <span>{{i + 1}} : {{todo.text}}</span>
        <button class="del-button" @click="deleteTodo(i)">Delete</button>
       </li>
     </ul>
        </div>
  </div>
</template>

<style>
@import './assets/base.css';

</style>
