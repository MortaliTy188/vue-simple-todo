<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>
<script>
export default {
  name: 'my-button',
}
</script>
<style>
.btn {
  padding: 12px 16px;
  border: 1px solid teal;
  border-radius: 4px;
  background-color: transparent;
  cursor: pointer;
  transition: background-color 0.3s;
}

.btn:hover {
  background-color: teal;
  color: white;
}
</style>
