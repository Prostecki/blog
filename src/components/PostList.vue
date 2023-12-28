<template>
  <!-- Section wrapper for the list of posts -->
  <section class="wrapper">

    <!-- CreatePostForm component with CreatePostButton as a child -->
    <CreatePostForm @addPost="addPost" />

    <!-- Loop through each post and render the PostCard component -->
    <article class="postList" v-for="post in reversedPosts" :key="post.id">

      <!-- Pass the current post as a prop to the PostCard component -->
      <PostCard :post="post" @deletePost="deletePost(post.id)"/>

    </article>
  </section>
</template>

<script>
// Importing the PostCard component
import CreatePostForm from './CreatePostForm.vue';
import PostCard from './PostCard.vue';

export default {
  // Registering the PostCard component for use in this template
  components: {
    CreatePostForm,
    PostCard,
    CreatePostForm  // Duplicate registration of CreatePostForm component
  },
  // Component name and props definition (accepting an array of posts)
  name: "PostList",
  props: ['posts'],
  computed: {
    reversedPosts() {
      // Create a copy of the array and reverse it
      return [...this.posts].reverse();
    }
  },
  methods: {
    deletePost(postId) {
      // Emit the 'deletePost' event with the postId
      this.$emit('deletePost', postId);
    },
    // Method to add a new post
    addPost(newPost) {
      // Assign a unique id to the new post
      newPost.id = this.posts.length + 1;
      // Add the new post to the posts array
      this.posts.push(newPost);
      // Save posts to local storage whenever a new post is added
      localStorage.setItem("posts", JSON.stringify(this.posts));
    },
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.postList {
  width: 600px;
  margin: 10px 0;
  padding: 5px;
  border: .5px solid black;
  border-radius: 8px;
}
</style>
