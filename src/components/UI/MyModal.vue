<template>
  <div v-if="show" class="modal" @click="hideModal">
    <div @click.stop class="modal-content">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: "MyModal",
  props: {
    show: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    hideModal() {
      this.$emit('show', false);
    }
  }
}
</script>

<style scoped>

.modal {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  background: rgba(0, 0, 0, 0.5);
}

.modal-content {
  margin: auto;
  padding: 2rem;
  background: white;
  border-radius: 10px;
  min-width: 300px;
  min-height: 30px;
}
</style>