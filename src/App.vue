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
          // completed: true
        },
        {
          id: 2,
          text: 'Complete Vue Project',
          // completed: false
        },
        {
          id: 3,
          text: 'Run errands',
          // completed: false
        }
      ]
    }
  },
methods: {
  addTodo() {
    this.todos.push({
      id: this.todos.length + 1,
      text: this.newTodo,
      // completed: false
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
    <input class="input" placeholder="Add New Task" v-model="newTodo" />
    <input class="button" type="button" value="Add" @click="addTodo" />
    <ul>
      <li>
        <input type="checkbox" v-model="todos[0].completed" />
        <span>{{ todos[0].text }}</span>
        <input type="button" value="Delete" @click="deleteTodo(0)" />
      </li>
    </ul>
    <!-- <button class="button" v-on:click="addTodo()">Submit</button> -->
    <!-- <ul>
      <li v-for="(todo,i) in todos" :key="todo-list">
        <span>
          {{ i + 1 }} : {{ todo.text }}
      </span>
      <button class="delete-button" @click="deleteTodo(i)">Delete</button>
      </li>
      </ul>  -->
        </div>
  </div>
</template>

<style>
@import './assets/base.css';

</style>
