<template>
  <div class="todo-item" @click="markComplete">
    <transition name="fade" :duration="{ enter: 500, leave: 500 }">
      <p :class="{ 'completed': todoItem.completed }">{{ todoItem.title }}</p>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'ToDoItem',
  props: ["todoItem"],
  methods: {
    markComplete() {
      this.$emit('toggle-complete', this.todoItem.id);
    }
  }
}
</script>

<style scoped>
.todo-item {
  padding: 10px;
  cursor: pointer;
}

.completed {
  text-decoration: line-through;
  color: #888;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
