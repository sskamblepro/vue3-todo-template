<script setup>
// Imports should be kept so trainees know what to import
import TodoForm from "./components/TodoForm.vue";
import TodoList from "./components/TodoList.vue";

// State management for todos
// TODO: Create state management for todos using ref()

// TODO: Implement loading todos from localStorage

// TODO: Implement saving todos to localStorage using watchEffect

// TODO: Create a computed property for filtered todos

// TODO: Implement adding a new todo

// TODO: Implement deleting a todo

// TODO: Implement toggling todo completion status

// TODO: Implement editing todo title

// TODO: Implement clearing completed todos
</script>

<template>
  <div class="app-container">
    <div class="card">
      <header>
        <h1>Vue 3 Todo App</h1>
      </header>

      <main>
        <!-- TODO: Implement TodoForm with add-todo event -->
        <TodoForm />

        <div class="filters">
          <!-- TODO: Implement filter buttons with active classes -->
          <button>All</button>
          <button>Active</button>
          <button>Completed</button>
          <button class="clear">Clear completed</button>
        </div>

        <!-- TODO: Implement TodoList with events -->
        <TodoList :todos="[]" />

        <div class="info">
          <p>0 items</p>
        </div>

        <div class="empty-state">
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
