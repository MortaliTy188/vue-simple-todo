<template>
  <div>
    <p class="completed-todos">Completed Todos: {{ completedTodosCount }}</p>
  </div>
</template>
<script>
import { computed } from 'vue'
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  setup(props) {
    const completedTodosCount = computed(() => {
      return props.todos.filter((todo) => todo.completed).length
    })
    return {
      completedTodosCount,
    }
  },
}
</script>
<style>
.completed-todos {
  font-weight: bold;
  color: teal;
}
</style>
