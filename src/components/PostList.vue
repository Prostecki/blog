<template>
    <section class="wrapper">
        <article class="postList" v-for="post in posts" :key="post.id">
            <PostCard :post="post"/>
        </article>
    </section>
</template>

<script>

import PostCard from './PostCard.vue';

    export default {
        components: {
            PostCard,
        },
        name: "PostList",
        props: ['posts'] //It's array of posts
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