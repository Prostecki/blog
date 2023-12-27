<template>
    <div class="wrapper">
        <div class="createPostForm">

            <input v-model="newPost.name" placeholder="Your name" class="input" type="text">
            <input v-model="newPost.content" placeholder="Content" class="input" type="text">

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
                    name: '',
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
                if (this.newPost.name && this.newPost.content) {
                    const newPost = {
                        name: this.newPost.name,
                        content: this.newPost.content,
                    };
                        this.$emit('add-post', newPost); // Emit an event to add the new post
                        this.clearInputFields(); // Clear input fields after addin
                    } else {
                        // Handle error, e.g., show a message to the user
                        console.error('Name and content are required');
                    }
            },
            clearInputFields() {
                this.newPost.name = '';
                this.newPost.content = '';
            },
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