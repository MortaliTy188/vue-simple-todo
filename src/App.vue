<template>
  <div>
    <my-input v-model="newTodo.title" placeholder="Add new todo" />
    <my-button @click="addTodo">Add Todo</my-button>
    <my-select v-if="todos.length > 0" name="filter" id="filter" v-model="filter"></my-select>
    <my-button v-if="filteredTodos.some((todo) => todo.completed)" @click="clearCompleted">
      Clear Completed
    </my-button>
  </div>

  <todos :filtered-todos="filteredTodos" :remove-todo="removeTodo" />

  <todos-counter :todos="filteredTodos" />
</template>
<script>
import { computed } from 'vue'
import Todos from './components/Todos.vue'
import TodosCounter from './components/TodosCounter.vue'
import MySelect from './components/UI/MySelect.vue'
export default {
  components: {
    Todos,
    TodosCounter,
  },
  data() {
    return {
      todos: [],
      filter: 'all',
      newTodo: { id: 0, title: '', completed: false },
    }
  },
  computed: {
    filteredTodos() {
      if (this.filter === 'completed') {
        return this.todos.filter((todo) => todo.completed)
      } else if (this.filter === 'in-progress') {
        return this.todos.filter((todo) => !todo.completed)
      }
      return this.todos
    },
    completedTodosCounter: computed(() => {
      return this.todos.filter((todo) => todo.completed).length
    }),
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
<style></style>
