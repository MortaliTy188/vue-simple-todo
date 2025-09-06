<template>
  <div class="todos" v-for="todo in filteredTodos" :key="todo.id">
    <span :class="{ completed: todo.completed }">{{ todo.title }}</span>
    <input type="checkbox" v-model="todo.completed" />
    <button @click="removeTodo(todo)">Remove</button>
  </div>
</template>
<script>
export default {
  props: {
    filteredTodos: {
      type: Array,
      required: true,
    },
    removeTodo: {
      type: Function,
      required: true,
    },
  },
}
</script>
<style>
.completed {
  text-decoration: line-through;
}
</style>
