<template>
  <div id="app">
    <h1>Todo Form</h1>
    <AddTodo @addTodo="addTodo" />
    <TodoList :todos="todos" @deleteTodo="deleteTodo" @editTodo="editTodo" />
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue';
import TodoList from './components/TodoList.vue';

export default {
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(todoText) {
      if (todoText.trim() !== '') {
        this.todos.push({ id: this.todos.length + 1, text: todoText });
      }
    },
    deleteTodo(todoId) {
      this.todos = this.todos.filter((todo) => todo.id !== todoId);
    },
    editTodo(updatedTodo) {
      const index = this.todos.findIndex((todo) => todo.id === updatedTodo.id);
      this.todos.splice(index, 1, updatedTodo);
    },
  },
  components: {
    AddTodo,
    TodoList,
  },
};
</script>

<style>
    #app {
      width: 500px;
      margin: 0 auto;
      text-align: center;
      box-sizing: border-box;
      background-color: #c9d6e8;
      border-radius: 0.5rem;
      font-size: 2rem;
      padding: 15px;
    }
    body {
      /* background-color: #00b2c2; */
      font-family: system-ui, serif;
      padding-top: 50px;
    }
    h1 {
      font-family: system-ui, sans-serif;
    }
    input {
      font-size: 18px;
      padding: 0.60rem 1rem;
      border: none;
      outline: none;
    }
    button {
      font-size: 18px;
      margin-top: 15px;
      margin-left: 5px;
      border-radius: 7px;
      padding: 0.60rem 1rem;
      border: none;
    }
    li {
      text-decoration: none;
      list-style: none;
      font-size: 30px;
      margin-left: 5px;
      color: #f0f0f0;
    }
    button:hover {
      background-color: #1900ff;
      cursor: pointer;
    }
</style>