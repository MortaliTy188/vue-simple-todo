<template>
  <select :value="modelValue" @change="$emit('update:modelValue', $event.target.value)">
    <option value="all">All</option>
    <option value="completed">Completed</option>
    <option value="in-progress">In progress</option>
  </select>
</template>
<script>
export default {
  name: 'MySelect',
  props: {
    modelValue: {
      type: String,
      required: true,
    },
  },
  emits: ['update:modelValue'],
}
</script>
<style>
select {
  padding: 12px 16px;
  border: 1px solid teal;
  border-radius: 4px;
  background-color: transparent;
  cursor: pointer;
  transition: background-color 0.3s;
}

select:hover {
  background-color: teal;
  color: white;
}
</style>
