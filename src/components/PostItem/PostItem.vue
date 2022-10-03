<template>
  <div class="post">
    <div>
      <div><strong>Name:</strong> {{ post.title }}</div>
      <div><strong>Description:</strong> {{ post.body}}</div>
    </div>
    <div class="list_btn">
      <MyButton @click="$emit('delete', post)">Delete</MyButton>
    </div>
  </div>
</template>

<script>

export default {
  name: "PostItem",
  props: {
    post: {
      type: Object,
      required: true,
    }
  }
}
</script>

<style scoped>

.post {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem;
  border: 2px solid teal;
  margin-top: 1rem;
}

.btn {
  margin-left: 1rem;
}

</style>