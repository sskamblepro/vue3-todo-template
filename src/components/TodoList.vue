<script setup>
import TodoItem from "./TodoItem.vue";

// Define props
const props = defineProps({
  todos: {
    type: Array,
    required: true,
  },
});

// Define emits
const emit = defineEmits(["delete-todo", "toggle-todo", "edit-todo"]);

// Handlers to forward events from TodoItem
const handleDelete = (id) => emit("delete-todo", id);
const handleToggle = (id) => emit("toggle-todo", id);
const handleEdit = (id, newTitle) => emit("edit-todo", id, newTitle);
</script>

<template>
  <div class="todo-list-container">
    <transition-group name="todo-list" tag="ul" class="todo-list">
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @delete-todo="handleDelete"
        @toggle-todo="handleToggle"
        @edit-todo="handleEdit"
      />
    </transition-group>
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
