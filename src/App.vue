<script>
export default {
  name: "app",
  data() {
    return {
      newTodo: "",
      todos: [
        {
          id: 1,
          text: "Buy Flowers",
          completed: true,
        },
        {
          id: 2,
          text: "Complete Vue Project",
          completed: false,
        },
        {
          id: 3,
          text: "Take a break",
          completed: false,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.length == 0) {
        return;
      }
      this.todos.push({
        id: this.todos.length + 1,
        text: this.newTodo,
        completed: false,
      });
      this.newTodo = "";
    },
    deleteTodo(i) {
      this.todos.splice(i, 1);
    },
  },
};
</script>

<template>
  <div id="app">
    <div id="container">
      <h1>June Todo List:</h1>
      <div>
        <input
          type="text"
          class="input"
          placeholder="Add New Task"
          v-model="newTodo"
          v-on:keyup.enter="addTodo"
        />
        <button class="add-button" v-on:click="addTodo()">Submit</button>
        <ul>
          <li v-for="(todo, i) in todos">
            <input
              type="checkbox"
              v-model="todo.completed"
              @click="completed = !completed"
              v-on:keyup.enter="completed"
            />
            <span>{{ i + 1 }}.{{ todo.text }}</span>

            <button class="edit-button" @click="editTodo(i)">Edit</button>
            <button
              class="del-button"
              @click="deleteTodo(i)"
              v-on:keyup.delete="deleteTodo"
            >
              Delete
            </button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style>
@import "./assets/base.css";
</style>
