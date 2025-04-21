<script setup>
import { ref, computed, watchEffect, onMounted } from "vue";
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";

// State management for todos
const todos = ref([]);
const filter = ref("all"); // all, active, completed

// Load todos from localStorage
onMounted(() => {
  const savedTodos = localStorage.getItem("vue3-todos");
  if (savedTodos) {
    todos.value = JSON.parse(savedTodos);
  }
});

// Save todos to localStorage whenever they change
watchEffect(() => {
  localStorage.setItem("vue3-todos", JSON.stringify(todos.value));
});

// Computed property for filtered todos
const filteredTodos = computed(() => {
  if (filter.value === "active") {
    return todos.value.filter((todo) => !todo.completed);
  } else if (filter.value === "completed") {
    return todos.value.filter((todo) => todo.completed);
  }
  return todos.value;
});

// Add a new todo
const addTodo = (title) => {
  if (title.trim()) {
    todos.value.push({
      id: Date.now(),
      title,
      completed: false,
      createdAt: new Date().toISOString(),
    });
  }
};

// Delete a todo
const deleteTodo = (id) => {
  todos.value = todos.value.filter((todo) => todo.id !== id);
};

// Toggle todo completion status
const toggleTodo = (id) => {
  const todo = todos.value.find((todo) => todo.id === id);
  if (todo) {
    todo.completed = !todo.completed;
  }
};

// Edit todo title
const editTodo = (id, newTitle) => {
  const todo = todos.value.find((todo) => todo.id === id);
  if (todo && newTitle.trim()) {
    todo.title = newTitle;
  }
};

// Clear all completed todos
const clearCompleted = () => {
  todos.value = todos.value.filter((todo) => !todo.completed);
};
</script>

<template>
  <div class="app-container">
    <div class="card">
      <header>
        <h1>Vue 3 Todo App</h1>
      </header>

      <main>
        <TodoForm @add-todo="addTodo" />

        <div class="filters">
          <button @click="filter = 'all'" :class="{ active: filter === 'all' }">
            All
          </button>
          <button
            @click="filter = 'active'"
            :class="{ active: filter === 'active' }"
          >
            Active
          </button>
          <button
            @click="filter = 'completed'"
            :class="{ active: filter === 'completed' }"
          >
            Completed
          </button>
          <button
            class="clear"
            @click="clearCompleted"
            v-if="todos.some((todo) => todo.completed)"
          >
            Clear completed
          </button>
        </div>

        <TodoList
          :todos="filteredTodos"
          @delete-todo="deleteTodo"
          @toggle-todo="toggleTodo"
          @edit-todo="editTodo"
        />

        <div class="info" v-if="todos.length > 0">
          <p>
            {{ filteredTodos.length }} items{{
              filter !== "all" ? " " + filter : ""
            }}
          </p>
        </div>

        <div class="empty-state" v-else>
          <p>No todos yet. Add one above!</p>
        </div>
      </main>

      <footer>
        <p>Double-click on a todo to edit</p>
      </footer>
    </div>
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap");

:root {
  --primary-color: #42b883;
  --secondary-color: #35495e;
  --bg-color: #f8f9fa;
  --card-bg: #ffffff;
  --text-color: #000000; /* Changed to black */
  --light-gray: #e9ecef;
  --border-color: #dee2e6;
  --shadow: 0 4px 20px rgba(0, 0, 0, 0.08);
  --card-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
  --radius: 8px;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Poppins", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen, Ubuntu, Cantarell, "Open Sans", sans-serif;
  background-color: var(--bg-color);
  color: var(--text-color);
  line-height: 1.6;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  padding: 2rem 1rem;
}

.app-container {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  padding: 2rem 0;
}

.card {
  background-color: var(--card-bg);
  border-radius: 16px;
  box-shadow: var(--card-shadow);
  width: 1080px;
  max-width: 1080px;
  padding: 3rem; /* Increased from 2rem to 3rem */
  margin: 0 auto;
}

header {
  text-align: center;
  margin-bottom: 2rem;
}

header h1 {
  color: var(--primary-color);
  font-size: 2.5rem;
  font-weight: 600;
  letter-spacing: -0.5px;
}

.filters {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
  flex-wrap: wrap;
}

button {
  background: white;
  border: 1px solid var(--border-color);
  border-radius: var(--radius);
  padding: 0.5rem 1rem;
  font-size: 0.875rem;
  font-family: "Poppins", sans-serif;
  cursor: pointer;
  transition: all 0.2s ease;
  color: var(--text-color); /* Ensuring black text for buttons */
}

button:hover {
  background-color: var(--light-gray);
}

button.active {
  background-color: var(--primary-color);
  color: white;
  border-color: var(--primary-color);
}

button.clear {
  margin-left: auto;
  color: #dc3545;
  border-color: #dc3545;
}

button.clear:hover {
  background-color: #dc3545;
  color: white;
}

.info {
  margin-top: 1rem;
  color: #000000; /* Changed to black */
  font-size: 0.875rem;
  text-align: center;
}

.empty-state {
  text-align: center;
  padding: 2rem;
  color: #000000; /* Changed to black */
  font-style: italic;
}

footer {
  margin-top: 2rem;
  text-align: center;
  font-size: 0.75rem;
  color: #000000; /* Changed to black */
}

@media (max-width: 640px) {
  .card {
    padding: 2rem; /* Increased from 1.5rem to 2rem */
  }
}
</style>
