<script setup>
// TODO: Import necessary Vue functions

// TODO: Define emits for add-todo event

// TODO: Create reactive state for new todo

// TODO: Implement submit todo method
</script>

<template>
  <form class="todo-form">
    <!-- TODO: Implement form submission and input binding -->
    <input
      type="text"
      placeholder="What needs to be done?"
      autofocus
      class="todo-input"
    />
    <button type="submit" class="add-button">Add</button>
  </form>
</template>

<style scoped>
.todo-form {
  display: flex;
  margin-bottom: 1.5rem;
  gap: 0.5rem;
}

.todo-input {
  flex: 1;
  padding: 0.75rem 1rem;
  font-size: 1rem;
  font-family: "Poppins", sans-serif;
  border: 2px solid var(--border-color);
  border-radius: var(--radius);
  transition: border-color 0.2s ease;
  outline: none;
  background-color: var(--bg-color);
  color: #000000;
}

.todo-input::placeholder {
  color: rgba(0, 0, 0, 0.5);
}

.add-button {
  background-color: var(--primary-color);
  color: white;
  border: none;
  padding: 0.75rem 1.5rem;
  font-weight: 600;
  border-radius: var(--radius);
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.add-button:hover:not(:disabled) {
  background-color: #3aa876;
}

.add-button:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
</style>
