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
<style></style>
