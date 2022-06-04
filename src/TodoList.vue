<script>
export default {
  name: "app",
  data() {
    return {
      newTodo: "",
      editing: false,
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
        editing: false,
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
    <div id="container"></div>
    <h1>June Todo List:</h1>
    <form @submit.prevent="addTodo">
      <input class="input" v-model="newTodo" />
      <button class="add-button">Add</button>
    </form>
    <ul class="list">
      <div class="list-group">
        <li v-for="todo in todos" :key="todo.id">
          <input class="checkbox" type="checkbox" v-model="todo.completed" />
          <span v-if="!todo.editing" :class="{ completed: todo.completed }">{{
            todo.text
          }}</span>
          <input
            class="form-2"
            v-if="todo.editing"
            style="display: inline"
            type="text"
            v-model="todo.text"
          />
          <button
            class="edit-button"
            v-if="!todo.editing"
            @click="todo.editing = true"
          >
            Edit
          </button>
          <button
            class="edit-button"
            v-if="todo.editing"
            @click="todo.editing = false"
          >
            Update
          </button>
          <button class="del-button" @click="deleteTodo(i)">Delete</button>
        </li>
      </div>
    </ul>
  </div>
</template>
