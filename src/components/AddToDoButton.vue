<template>
  
  <div class="add-todo">
    <form @submit.prevent="addToDo">
      <input type="text" v-model.trim="title" placeholder="Add a new task">
      <button type="submit">Add</button>
    </form>
  </div>
  
</template>

<script>
import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'AddToDoButton',
  data() {
    return {
      title: ""
    }
  },
  methods: {
    addToDo() {
      if (this.title.trim()) {
        const newToDoObject = {
          id: uuidv4(),
          title: this.title,
          completed: false
        }
        this.$emit("add-todo-event", newToDoObject);
        this.title = '';
      }
    }
  }
}
</script>

<style scoped>
.add-todo {
  margin-top: 20px;
}

input[type="text"] {
  padding: 8px;
  width: 200px;
  border: 1px solid #ccc;
  border-radius: 4px;
  margin-right: 8px;
}

button {
  padding: 8px 16px;
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>
