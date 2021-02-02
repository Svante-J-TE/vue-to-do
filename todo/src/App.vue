<template>
  <div id="app">
    <div>
      <input type="text" id="todoInput" />
      <button @click="addTodoItem()">Add to list</button>
      <button @click="clearAllItems()">Clear list</button>
    </div>
    <div v-for="item in todoItems" :key="item.todo">
      <TodoList :title="item.todo" :isDone="item.isDone" />
      <button @click="removeItem(item.id)">remove this item</button>
      <button @click="markAsDone(item.id)" id="isDoneBtn">Mark this item as done</button>
    </div>
  </div>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: "App",
  components: {
    TodoList,
  },
  data() {
    return {
      todoItems: [],
    };
  },
  methods: {
    addTodoItem() {
      this.todoItems.push({
        todo: document.getElementById("todoInput").value,
        id: this.todoItems.length,
        isDone: false,
      });
    },
    removeItem(id) {
      for (var i = 0; i < this.todoItems.length; i++) {
        if (this.todoItems[i].id == id) {
          this.$delete(this.todoItems, i);
          break;
        }
      }
    },
    clearAllItems() {
      this.todoItems = [];
    },
    markAsDone(id) {
      for (var i = 0; i < this.todoItems.length; i++) {
        if (this.todoItems[i].id == id) {
          if (this.todoItems[i].isDone == false) {
            this.todoItems[i].isDone = true;
            document.getElementById("isDoneBtn").innerHTML = "Mark this item as not done";
          } else {
            this.todoItems[i].isDone = false;
            document.getElementById("isDoneBtn").innerHTML = "Mark this item as done";
          }
        }
      }
    },
  },
};
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
