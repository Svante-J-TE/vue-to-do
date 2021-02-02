<template>
  <div id="app">
    <div>
      <input type="text" id="todoInput">
      <button @click="addTodoItem()">Add to list</button>
      <button @click="clearAllItems()">Clear list</button>

    </div>
    <div v-for="item in todoItems" :key="item.todo">
      <TodoList :title="item.todo"/>
    </div>
  </div>
</template>

<script>
import TodoList from './components/TodoList'

export default {
  name: 'App',
  components: {
    TodoList
  },
    data(){
    return{
      todoItems: []
    }
  },
  methods: {
    addTodoItem(){
      this.todoItems.push(
        {todo: document.getElementById("todoInput").value}
      );
    },
    clearAllItems(){
      this.todoItems = []
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
</style>
