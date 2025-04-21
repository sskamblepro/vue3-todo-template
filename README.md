# Vue 3 Todo App - Training Template

This is a training template for learning Vue 3 with the Composition API. The template provides all the necessary styling and structure, but the functionality has been stripped out for training purposes.

## Project Goal

Build a fully functional Todo application with the following features:
- Add new todos
- Delete todos
- Toggle todo completion status
- Edit existing todos
- Filter todos (all, active, completed)
- Clear completed todos
- Persist todos to localStorage

## Getting Started

1. Install dependencies:
```bash
npm install
```

2. Start the development server:
```bash
npm run dev
```

## Implementation Tasks

Follow these steps to implement the functionality:

### 1. App.vue
- Create state management for todos using ref()
- Implement loading todos from localStorage
- Implement saving todos using watchEffect
- Create computed property for filtered todos
- Implement todo CRUD operations (Create, Read, Update, Delete)
- Implement filter functionality
- Implement clear completed functionality

### 2. TodoForm.vue
- Create state for new todo input
- Define emit for add-todo event
- Implement form submission

### 3. TodoList.vue
- Define props for todos array
- Define emits for todo operations
- Implement event handlers
- Loop through todos to render TodoItem components

### 4. TodoItem.vue
- Define props for individual todo objects
- Define emits for todo operations
- Implement edit mode toggling
- Implement date formatting
- Handle todo actions (toggle, edit, delete)

## Learning Resources

- [Vue 3 Documentation](https://vuejs.org/guide/introduction.html)
- [Vue 3 Composition API](https://vuejs.org/api/composition-api-setup.html)
- [Vue 3 Template Syntax](https://vuejs.org/guide/essentials/template-syntax.html)
