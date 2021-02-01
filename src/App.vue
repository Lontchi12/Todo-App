<template>
  <div class="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" v-on:todo-done="clearCompleted"/>
  <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
  
</template>

<script>

import Header from "./components/layout/Header"
import AddTodo from "./components/AddTodo"
import Todos from "./components/Todos"


export default {
  name: 'App',
  components: {
    Header,
    AddTodo,
    Todos,
    
    
    
  },
  data() {
    return {
      todos:[
        {
          id: 1,
          title: "Todo one",
          completed: false
        },
        {
          id: 2,
          title: "Todo two",
          completed: true
        },
        {
          id: 3,
          title: "Todo three",
          completed: false
        }
        
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
    },
    clearCompleted(isComplete) {
      this.todos = this.todos.filter(isComplete);
    },
    clearAll() {
      this.todos = [];
    }
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
  background: aquamarine;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
.app {
  width: 500px;
  margin-left: 100px;
  margin-top: 100px;
  background: #fff;
}
</style>
