<template>

  <div class="app">
    <Header />

    <PostList :posts="posts" />

    <Footer />

    <CreatePostForm>

      <CreatePostButton />

    </CreatePostForm>
  </div>

</template>

<script>
  
  import Header from "@/components/Header.vue";
  import PostList from "@/components/PostList.vue";
  import Footer from "@/components/Footer.vue";
  import CreatePostForm from "@/components/CreatePostForm.vue";
  import CreatePostButton from "@/components/UI/CreatePostButton.vue";

  export default {
    components: {
      Header,
      PostList,
      Footer,
      CreatePostForm,
      CreatePostButton,
    },
    data() {
        return {
            // Initial array of posts
            posts: [
                {id: 1, title: 'First post', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.'},
                {id: 2, title: 'Second post',content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.'},
                {id: 3, title: 'Third post', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.'},
                {id: 4, title: 'Fourth post', content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin quam tortor, egestas id pharetra interdum.'}
            ],
      };
    },
    methods: {
      openCreatePostForm() {
        this.showCreatePostForm = true;
      }
    }
  }
  
</script>

<style scoped>

  .app {
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    width: 1200px;
    height: 100vh;
    margin: 0 auto;
  }

</style>
