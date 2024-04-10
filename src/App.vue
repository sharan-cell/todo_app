<template>
  <div class="main-container">
    <ToDo
      :todoEntries="todoEntries"
      @remove-todo="removeToDoItem"
    />
    <AddToDoButton @add-todo-event="addToDoItem"/>
  </div>
</template>

<script>
import ToDo from './components/ToDo.vue'
import AddToDoButton from './components/AddToDoButton.vue'

export default {
  name: 'App',
  components: {
    ToDo,
    AddToDoButton
  },
  data() {
    return {
      todoEntries: [
        {
          id: 1,
          title: "Go to Groceries",
          completed: false
        },
        {
          id: 2,
          title: "Work on integration",
          completed: false
        },
        {
          id: 3,
          title: "Learn vue.js",
          completed: false
        }
      ]
    }
  },
  methods: {
    addToDoItem(newToDoItem) {
      this.todoEntries = [...this.todoEntries, newToDoItem];
    },
    removeToDoItem(todoId) {
      this.todoEntries = this.todoEntries.filter(todo => todo.id !== todoId);
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
