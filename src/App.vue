<template>
  <div class="app">
    <MyButton @click="showModal">Create new post</MyButton>
    <MyModal v-model:show="isModalVisible" @show="showModal">
      <PostForm @create="createPost" />
    </MyModal>
    <PostList :posts="posts" @delete="deletePost"/>
  </div>
</template>

<script>
import PostList from "@/components/PostList/PostList.vue";
import PostForm from "@/components/PostForm/PostForm.vue";

export default {
  components: {
    PostList,
    PostForm,
  },
  data() {
    return {
      posts: [
        { id: 1, title: "JavaScript", description: "post description" },
        { id: 2, title: "JavaScript 2", description: "post description 2" },
        { id: 3, title: "JavaScript 3", description: "post description 3" },
        { id: 4, title: "JavaScript 4", description: "post description 4" },
        { id: 5, title: "JavaScript 5", description: "post description 5" },
      ],
      isModalVisible: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.isModalVisible = false;
    },
    deletePost(post) {
      this.posts = this.posts.filter(v => v.id !== post.id);
    },
    showModal(value) {
      this.isModalVisible = !value ? value : true;
    },
  }
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 2rem;
}

</style>
