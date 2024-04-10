<template>
  <div class="todo-list">
    <ul>
      <ToDoItem
        v-for="todo in todoEntries"
        :key="todo.id"
        :todoItem="todo"
        @toggle-complete="handleToggleComplete"
      />
    </ul>
  </div>
</template>

<script>
import ToDoItem from './ToDoItem.vue'

export default {
  name: 'ToDo',
  components: {
    ToDoItem
  },
  props: ["todoEntries"],
  methods: {
    handleToggleComplete(todoId) {
      this.$emit('remove-todo', todoId);
    }
  }
}
</script>

<style scoped>
.todo-list {
  margin-top: 20px;
}
</style>
