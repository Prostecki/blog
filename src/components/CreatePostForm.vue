<template>
    <div class="wrapper">
        <div class="createPostForm">

            <input v-model="newPost.title" placeholder="Write something..." class="input" type="text">

            <button class="addPost">

                <AnOutlinedPlus @click="addNewPost" class="animate" />

            </button>

        </div>
    </div>
</template>

<script>
    import { AnOutlinedPlus } from "@kalimahapps/vue-icons";
    export default {
        data() {
            return {
                newPost: {
                    title: '',
                    content: '',
                }
            }
        },
        name: "CreatePostForm",
        components: {
            AnOutlinedPlus
        },
        methods: {
            addNewPost() {
                this.$emit("addPost", this.newPost);
                this.newPost.title = '';
                this.newPost.content = '';
            }
        }
    }
</script>

<style scoped>

    .wrapper {
        position: relative;
        width: 100%;
        display: flex;
        justify-content: center;
    }
    .createPostForm {
        display: flex;
        justify-content: center;
        width: 500px;
        padding: 5px;
        /* border-radius: 12px; */
        border: .5px solid grey;
    }
    .input {
        margin: 0 10px;
        padding: 5px;
    }
     .addPost {
        line-height: 10px;
        border: none;
        cursor: pointer;
        transition: .4s;
     }
     .animate {
        width: 25px;
        padding: 10px;
        transition: .4s;
     }
     .animate:hover {
        background-color: teal;
        transition: .4s;
        color: white;
     }
</style>