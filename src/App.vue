<template>
  <div>
    <input type="text" v-model="newTodo.title" placeholder="Add new todo" />
    <button @click="addTodo">Add Todo</button>
    <select name="filter" id="filter" v-model="filter">
      <option value="all">All</option>
      <option value="completed">Completed</option>
      <option value="in-progress">In progress</option>
    </select>
    <button v-if="filteredTodos.some((todo) => todo.completed)" @click="clearCompleted">
      Clear Completed
    </button>
  </div>

  <div class="todos" v-for="todo in filteredTodos" :key="todo.id">
    <span :class="{ completed: todo.completed }">{{ todo.title }}</span>
    <input type="checkbox" v-model="todo.completed" />
    <button @click="removeTodo(todo)">Remove</button>
  </div>

  <div>
    <p>Completed Todos: {{ completedTodosCounter }}</p>
  </div>
</template>
<script>
import { computed } from 'vue'

export default {
  data() {
    return {
      todos: [
        { id: 1, title: 'Task 1', completed: false },
        { id: 2, title: 'Task 2', completed: false },
        { id: 3, title: 'Task 3', completed: false },
      ],
      filter: 'all',
      completedTodosCounter: computed(() => {
        return this.todos.filter((todo) => todo.completed).length
      }),
      newTodo: { id: 0, title: '', completed: false },
      filteredTodos: computed(() => {
        if (this.filter === 'completed') {
          return this.todos.filter((todo) => todo.completed)
        } else if (this.filter === 'in-progress') {
          return this.todos.filter((todo) => !todo.completed)
        }
        return this.todos
      }),
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.title.trim()) {
        this.todos.push({ ...this.newTodo })
        this.newTodo = { id: Date.now(), title: '', completed: false }
      }
    },
    removeTodo(todo) {
      this.todos = this.todos.filter((t) => t.id !== todo.id)
    },
    clearCompleted() {
      this.todos = this.todos.map((todo) => {
        if (todo.completed) {
          return { ...todo, completed: false }
        }
        return todo
      })
    },
  },
}
</script>
<style>
.completed {
  text-decoration: line-through;
}
</style>
