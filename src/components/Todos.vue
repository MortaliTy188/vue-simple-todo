<template>
  <div class="todos" v-for="todo in filteredTodos" :key="todo.id">
    <div class="todo">
      <span :class="{ completed: todo.completed }">{{ todo.title }}</span>
      <input type="checkbox" v-model="todo.completed" />
    </div>
    <button class="btn" @click="removeTodo(todo)">Remove</button>
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

.todos {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 12px 16px;
  border-bottom: 1px solid #eee;
  gap: 30px;
  border: 1px solid teal;
  border-radius: 20px;
  width: 80%;
}

.todo {
  display: flex;
  align-items: center;
  gap: 10px;
}
</style>
