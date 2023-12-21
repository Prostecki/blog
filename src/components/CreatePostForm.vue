<template>
    <div class="wrapper">
        <div class="createPostForm">
            <input type="text">
            <button class="addPost">+</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "CreatePostForm"
    }
</script>

<style scoped>

    .wrapper {
        position: relative;
        width: 100%;
        background-color: rgba(0, 0, 0, 0.5);
    }
    .createPostForm {
        position: absolute;
        top: 30%;
        right: 30%;
        width: 500px;
        height: 300px;
        padding: 5px;
        background-color: yellow;
        border-radius: 12px;
        border: .5px solid grey;
    }
     .addPost {
        width: 50px;
        padding: 5px;
        color: white;
        background-color: teal;

     }
</style>