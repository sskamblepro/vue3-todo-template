<script setup>
import TodoItem from "./TodoItem.vue";

// TODO: Define props for todos

// TODO: Define emits for delete-todo, toggle-todo, and edit-todo

// TODO: Implement event handlers for TodoItem events
</script>

<template>
  <div class="todo-list-container">
    <ul class="todo-list">
      <!-- TODO: Implement todo list rendering with TodoItem component -->
      <TodoItem />
    </ul>
  </div>
</template>

<style scoped>
.todo-list-container {
  margin-bottom: 1.5rem;
  font-family: "Poppins", sans-serif;
}

.todo-list {
  list-style: none;
  padding: 0;
}

.todo-list-enter-active,
.todo-list-leave-active {
  transition: all 0.5s ease;
}

.todo-list-enter-from {
  opacity: 0;
  transform: translateX(30px);
}

.todo-list-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}
</style>
