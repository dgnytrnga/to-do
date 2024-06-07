<template>
    <div>
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo" />
      <ul>
        <li v-for="(todo, index) in todos" :key="index">
          <span :class="{ done: todo.done }" @click="toggleDone(index)">{{ todo.text }}</span>
          <button @click="removeTodo(index)">x</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: '',
        todos: []
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.todos.push({ text: this.newTodo, done: false });
          this.newTodo = '';
        }
      },
      toggleDone(index) {
        this.todos[index].done = !this.todos[index].done;
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      }
    }
  };
  </script>
  
  <style>
  .done {
    text-decoration: line-through;
  }
  ul {
    list-style-type: none;
    padding: 0;
  }
  li {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  input {
    padding: 1em;
    margin-bottom: 1em;
    width: 100%;
    box-sizing: border-box;
  }
  button {
    background: none;
    border: none;
    color: green;
    cursor: pointer;
  }
  button:focus {
    outline: none;
  }
  </style>
  