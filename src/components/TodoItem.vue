<script setup>
import { ref, nextTick } from "vue";

// Define props
const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
});

// Define emits
const emit = defineEmits(["delete-todo", "toggle-todo", "edit-todo"]);

// Local state for edit mode
const isEditing = ref(false);
const editedTitle = ref(props.todo.title);
const editInput = ref(null);

// Toggle edit mode
const startEditing = () => {
  isEditing.value = true;
  editedTitle.value = props.todo.title;

  // Focus the input after DOM update
  nextTick(() => {
    editInput.value.focus();
  });
};

// Save edited todo
const saveEdit = () => {
  if (editedTitle.value.trim() !== props.todo.title) {
    emit("edit-todo", props.todo.id, editedTitle.value);
  }
  isEditing.value = false;
};

// Cancel edit mode
const cancelEdit = () => {
  isEditing.value = false;
  editedTitle.value = props.todo.title;
};

// Format date
const formatDate = (dateString) => {
  const options = {
    month: "short",
    day: "numeric",
    hour: "2-digit",
    minute: "2-digit",
  };
  return new Date(dateString).toLocaleDateString(undefined, options);
};
</script>

<template>
  <li class="todo-item" :class="{ completed: todo.completed }">
    <!-- View Mode -->
    <div v-if="!isEditing" class="todo-item-view">
      <div class="todo-content">
        <input
          type="checkbox"
          :checked="todo.completed"
          @change="emit('toggle-todo', todo.id)"
          class="todo-checkbox"
        />
        <div class="todo-details" @dblclick="startEditing">
          <span class="todo-title">{{ todo.title }}</span>
          <small class="todo-date" v-if="todo.createdAt">
            {{ formatDate(todo.createdAt) }}
          </small>
        </div>
      </div>
      <div class="todo-actions">
        <button class="edit-btn" @click="startEditing" title="Edit todo">
          ✏️
        </button>
        <button
          class="delete-btn"
          @click="emit('delete-todo', todo.id)"
          title="Delete todo"
        >
          🗑️
        </button>
      </div>
    </div>

    <!-- Edit Mode -->
    <div v-else class="todo-item-edit">
      <input
        ref="editInput"
        v-model="editedTitle"
        @blur="saveEdit"
        @keyup.enter="saveEdit"
        @keyup.esc="cancelEdit"
        class="edit-input"
      />
    </div>
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
