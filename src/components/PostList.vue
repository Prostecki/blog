<template>
    <!-- Section wrapper for the list of posts -->

    <section class="wrapper">
      <!-- Loop through each post and render the PostCard component -->

      <article class="postList" v-for="post in posts" :key="post.id">
        <!-- Pass the current post as a prop to the PostCard component -->
        <PostCard :post="post"/>

      </article>
    </section>
  </template>
  
  <script>

  // Importing the PostCard component
  import PostCard from './PostCard.vue';
  
  export default {
    // Registering the PostCard component for use in this template
    components: {
      PostCard,
    },
    // Component name and props definition (accepting an array of posts)
    name: "PostList",
    props: ['posts']
  }
  </script>
  
  <style scoped>
    .wrapper {
      text-align: center;
    }

    .postList {
      margin: 10px 0;
      padding: 5px;
      border: .5px solid black;
    }
  </style>
  