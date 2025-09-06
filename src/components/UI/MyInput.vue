<template>
  <input
    class="input"
    type="text"
    :value="modelValue"
    @input="updateInput"
    @keydown.enter="$emit('enter')"
  />
</template>
<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    },
  },
  emits: {
    'update:modelValue': null,
  },
}
</script>
<style>
.input {
  padding: 12px 16px;
  border: 1px solid teal;
  border-radius: 4px;
  width: 100%;
  max-width: 400px;
  background-color: transparent;
}

.input:focus {
  outline: none;
  border-color: darkcyan;
}
</style>
