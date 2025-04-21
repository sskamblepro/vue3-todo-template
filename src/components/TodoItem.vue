<script setup>
// TODO: Import necessary Vue functions

// TODO: Define props for todo item

// TODO: Define emits for delete-todo, toggle-todo, and edit-todo events

// TODO: Implement local state for edit mode

// TODO: Implement methods for edit functionality

// TODO: Implement date formatting
</script>

<template>
  <li class="todo-item">
    <!-- View Mode -->
    <div class="todo-item-view">
      <div class="todo-content">
        <!-- TODO: Implement checkbox functionality -->
        <input
          type="checkbox"
          class="todo-checkbox"
        />
        <div class="todo-details">
          <!-- TODO: Add double-click event for editing -->
          <span class="todo-title">Example Todo Item</span>
          <!-- TODO: Implement date display -->
          <small class="todo-date">Apr 21</small>
        </div>
      </div>
      <div class="todo-actions">
        <!-- TODO: Implement edit and delete functionality -->
        <button class="edit-btn" title="Edit todo">✏️</button>
        <button class="delete-btn" title="Delete todo">🗑️</button>
      </div>
    </div>

    <!-- Edit Mode -->
    <!-- TODO: Implement edit mode with conditional rendering -->
    <!-- <div class="todo-item-edit">
      <input
        class="edit-input"
      />
    </div> -->
  </li>
</template>

<style scoped>
.todo-item {
  background-color: white;
  border-radius: var(--radius);
  margin-bottom: 0.75rem;
  box-shadow: var(--shadow);
  overflow: hidden;
  transition: all 0.3s ease;
  border: 1px solid var(--border-color);
}

.todo-item.completed {
  opacity: 0.7;
}

.todo-item-view {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem;
}

.todo-content {
  display: flex;
  align-items: center;
  text-align: left;
  gap: 1rem;
  flex: 1;
}

.todo-checkbox {
  width: 1.25rem;
  height: 1.25rem;
  border-radius: 50%;
  cursor: pointer;
  accent-color: var(--primary-color);
}

.todo-details {
  display: flex;
  flex-direction: column;
  cursor: pointer;
  font-family: "Poppins", sans-serif;
}

.todo-title {
  font-size: 1rem;
  transition: text-decoration 0.3s ease;
  font-weight: 500;
  color: #000000;
}

.completed .todo-title {
  text-decoration: line-through;
  color: #000000;
  opacity: 0.6;
}

.todo-date {
  font-size: 0.75rem;
  color: #000000;
  margin-top: 0.25rem;
}

.todo-actions {
  display: flex;
  gap: 0.5rem;
}

.edit-btn,
.delete-btn {
  background: none;
  border: none;
  font-size: 1rem;
  cursor: pointer;
  opacity: 0.6;
  transition: opacity 0.2s ease;
  padding: 0.25rem;
}

.edit-btn:hover,
.delete-btn:hover {
  opacity: 1;
  background: none;
}

.todo-item-edit {
  padding: 0.5rem;
}

.edit-input {
  width: 100%;
  padding: 0.75rem;
  font-size: 1rem;
  border: 2px solid var(--primary-color);
  border-radius: var(--radius);
  outline: none;
  font-family: "Poppins", sans-serif;
  background-color: white;
  color: black;
}
</style>
