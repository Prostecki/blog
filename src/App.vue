<template>
  <!-- The root element of your Vue app -->
  <div class="app">
    
    <!-- Header component -->
    <Header @open-sidebar="openSideBar"/>
    
    <!-- SideBar component -->
    <SideBar :sidebarOpen="sidebarOpen" :close-sidebar="closeSidebar"/>

    <!-- CreatePostForm component with CreatePostButton as a child -->
    <CreatePostForm @addPost="addPost">
      <CreatePostButton />
    </CreatePostForm>

    <!-- PostList component with posts data passed as a prop -->
    <PostList :posts="posts" />

    <!-- Footer component -->
    <Footer />
    
  </div>
</template>

<script>
  // Importing necessary components
  import Header from "@/components/Header.vue";
  import SideBar from "@/components/SideBar.vue";
  import PostList from "@/components/PostList.vue";
  import Footer from "@/components/Footer.vue";
  import CreatePostForm from "@/components/CreatePostForm.vue";
  import CreatePostButton from "@/components/UI/CreatePostButton.vue";

  export default {
    // Registering components for use in this template
    components: {
      Header,
      SideBar,
      PostList,
      Footer,
      CreatePostForm,
      CreatePostButton,
    },
    data() {
      // Data property to hold the initial array of posts
      return {
        // Load posts from local storage or use a default array
        posts: JSON.parse(localStorage.getItem("posts")) || [
          { id: 1, title: 'First post', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.' },
          { id: 2, title: 'Second post', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.' },
          { id: 3, title: 'Third post', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.' }
        ],
        sidebarOpen: false,
      };
    },
    methods: {
      // Method to handle opening the CreatePostForm (assuming there's some missing code related to this)
      openCreatePostForm() {
        this.showCreatePostForm = true;
      },
      // Method to add a new post
      addPost(newPost) {
        newPost.id = this.posts.length + 1;
        this.posts.push(newPost);
        // Save posts to local storage whenever a new post is added
        localStorage.setItem("posts", JSON.stringify(this.posts));
      },
      // Method to open the sidebar
      openSideBar() {
        this.sidebarOpen = true;
      },
      // Method to close the sidebar
      closeSidebar() {
        this.sidebarOpen = false;
      }
    }
  }
</script>

<style scoped>
  /* Styling for the root app element */
  .app {
    margin: 0 auto;
  }

  @media screen and (max-width: 1000px) {
    .app {
      width: 100%;
      padding: 10px;
    }
  }
</style>
