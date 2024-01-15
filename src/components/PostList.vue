<template>
  <!-- Section wrapper for the list of posts -->
  <section class="wrapper">

    <!-- CreatePostForm component with CreatePostButton as a child -->
    <CreatePostForm :currentUser="currentUser" @addPost="addPost" />

    <!-- Loop through each post and render the PostCard component -->
    
    <article class="postList" v-for="post in reversedPosts" :key="post.id">

      <!-- Pass the current post as a prop to the PostCard component -->
      <transition name="fade" mode="out-in">

        <PostCard :post="post" @deletePost="deletePost(post.id)" />

      </transition>

    </article>

  </section>

</template>

<script>
// Importing the PostCard component
import CreatePostForm from './CreatePostForm.vue';
import PostCard from './PostCard.vue';

export default {
  data() {
    return {
      currentUser: null
    }
  },
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
    handleUserData(userData) {
      this.currentUser = userData;
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
  box-shadow: 5px 5px 10px #0000004d;
}
@keyframes fadeOut {
    from {
      opacity: 1;
      transform: translateY(0);
    }
    to {
      opacity: 0;
      transform: translateY(-100%);
    }
  }
  .fade-out {
    animation: fadeOut 0.5s ease forwards;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s, transform 0.5s;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
    transform: translateY(-100%);
  }
</style>
