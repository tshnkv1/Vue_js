<template>
  <div v-if="posts.length > 0">
    <h3>List of posts</h3>
    <PostItem
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @delete="$emit('delete', post)"
    />
  </div>
  <h3 v-else>List of posts is empty</h3>
</template>

<script>
import PostItem from "@/components/PostItem/PostItem.vue";

export default {
  name: 'PostList',
  components: {
    PostItem,
  },
  props: {
    posts: {
      type: Array,
      required: true,
    }
  },
}
</script>

<style scoped>

</style>