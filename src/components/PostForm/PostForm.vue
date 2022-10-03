<template>
  <h3>Creating post</h3>
  <form @submit.prevent>
    <MyInput v-model:value="post.title" placeholder="Name" />
    <MyInput v-model:value="post.description" placeholder="Description" />
    <MyButton @click="createPost">Add post</MyButton>
  </form>
</template>

<script>

export default {
  name: 'PostForm',
  props: {},
  data() {
    return {
      post: {
        title: '',
        description: '',
      }
    }
  },
  methods: {
    createPost() {
        this.post.id = Date.now();
        this.$emit('create', this.post);
        this.post = {
          title: '',
          description: '',
      };
    },
  }
}
</script>

<style scoped>

form {
  display: flex;
  flex-direction: column;
}

.btn {
  margin-top: 1rem;
  align-self: flex-end;
}

</style>