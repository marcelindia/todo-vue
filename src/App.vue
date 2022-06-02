<script>
// import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
export default {
  name: 'app',
  data() {
    return {
      newTodo: '',
      todos: [
        {
          id: 1,
          text: 'Learn Vue',
          completed: true
        },
        {
          id: 2,
          text: 'Complete Vue Project',
          completed: false
        },
        {
          id: 3,
          text: 'Run errands',
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
    <h1>List of Goals:</h1>
    <input class="input" v-model="newTodo" />
    <button class="button" v-on:click="addTodo()">Submit</button>
    <ul>
      <li v-for="(todo,i) in todos" :key="todo-id">
      <span>
        {{ i + 1 }} : {{ todo.text }}
      </span>
      <button class="delete-button" @click="deleteTodo(i)">Delete</button>
      </li>
      </ul> 
  </div>
</template>

<style>
@import './assets/base.css';

#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}


</style>
