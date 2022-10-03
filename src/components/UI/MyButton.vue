<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "MyButton"
}
</script>

<style scoped>

.btn {
  padding: 10px 1rem;
  border: 1px solid teal;
  background: none;
  color: teal;
  cursor: pointer;
}

</style>