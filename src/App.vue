<template>
  <div class="app">
    <h3>Create new post</h3>
    <MyButton @click="showModal">Create new post</MyButton>
    <MyModal v-model:show="isModalVisible" @show="showModal">
      <PostForm @create="createPost" />
    </MyModal>
    <PostList v-if="!isLoading" :posts="posts" @delete="deletePost"/>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import axios from 'axios';
import PostList from "@/components/PostList/PostList.vue";
import PostForm from "@/components/PostForm/PostForm.vue";

export default {
  components: {
    PostList,
    PostForm,
  },
  data() {
    return {
      posts: [],
      isModalVisible: false,
      isLoading: false,
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
    async fetchPosts() {
      this.isLoading = true;
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        this.posts = response.data;
      } catch(error) {
        console.error(error);
      } finally {
        this.isLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
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

.btn {
  margin: 1rem 0;
}

</style>
