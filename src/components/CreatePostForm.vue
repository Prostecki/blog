<template>
    <div class="wrapper">
        <div class="createPostForm">

            <input v-model="newPost.name" placeholder="Your name" class="input name" type="text">
            <textarea v-model="newPost.content" placeholder="What is happening?!" class="input content" type="text"></textarea>

            <div class="postform-actions">

                <div class="buttons-group">
                    <button class="postform-buttons">
                        <IcMediaImage class="animate" alt="Media" />
                    </button>
    
                    <button class="postform-buttons">
                        <AnOutlinedGif class="animate" />
                    </button>
    
                    <button class="postform-buttons">
                        <BxPoll class="animate" />
                    </button>
    
                    <button class="postform-buttons">
                        <FlEmojiEdit class="animate" />
                    </button>
                    <button class="postform-buttons">
                        <AkSchedule class="animate" />
                    </button>
                </div>

                <button class="postbutton" @click="addNewPost" :class="{ 'disabled': isEmpty }" :disabled="isEmpty">
                    post
                </button>
            </div>
        </div>
    </div>
</template>

<script>
    import { IcMediaImage } from "@kalimahapps/vue-icons";
    import { AnOutlinedGif } from "@kalimahapps/vue-icons";
    import { BxPoll } from "@kalimahapps/vue-icons";
    import { FlEmojiEdit } from "@kalimahapps/vue-icons";
    import { AkSchedule } from "@kalimahapps/vue-icons";

    export default {
        data() {
            return {
                newPost: {
                    name: '',
                    content: '',
                },
                isEmpty: true,
            }
        },
        name: "CreatePostForm",
        components: {
            IcMediaImage,
            AnOutlinedGif,
            BxPoll,
            FlEmojiEdit,
            AkSchedule,
        },
        watch: {
            // Watching changes in the 'newPost' property
            newPost: {
                // Handler function to be executed when 'newPost' changes
                handler(newVal) {
                    // Check if the 'name' or 'content' property of 'newPost' is empty after trimming
                    this.isEmpty = !newVal.name.trim() || !newVal.content.trim();
                },
                // Enable deep watching to track changes in nested object properties
                deep: true,
            },
        },
        methods: {
            addNewPost() {
                if (this.newPost.name && this.newPost.content) {
                    const newPost = {
                        name: this.newPost.name,
                        content: this.newPost.content,
                    };
                    this.$emit('add-post', newPost); // Emit an event to add the new post
                    this.clearInputFields(); // Clear input fields after adding
                } else {
                    // Handle error, e.g., show a message to the user
                    console.error('Name and content are required');
                    this.isEmpty = !this.isEmpty;
                    console.log(this.isEmpty);
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
        display: flex;
        justify-content: center;
        padding: 20px;
    }

    .createPostForm {
        width: 600px;
        border: 1px solid #ccd6dd;
        border-radius: 12px;
        padding: 20px;
        background-color: #fff;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }

    .input {
        border: 1px solid #ccd6dd;
        margin: 10px 0;
        padding: 12px;
        border-radius: 8px;
        width: 100%;
        box-sizing: border-box;
        font-size: 14px;
    }

    .name {
        width: calc(100% - 24px);
    }

    .content {
        width: calc(100% - 24px);
        resize: none;
    }

    .postform-actions {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-top: 15px;
    }

    .postform-buttons {
        line-height: 1;
        border: none;
        cursor: pointer;
        transition: background-color 0.4s, color 0.4s;
        background: none;
        padding: 0;
        font-size: 16px;
        color: #66757f;
    }

    .postform-buttons:hover {
        background-color: #e1f2fe;
        color: #1da1f2;
    }

    .postbutton {
        width: 100px;
        border: none;
        cursor: pointer;
        border-radius: 9999px;
        transition: background-color 0.4s, color 0.4s;
        padding: 10px;
        font-size: 14px;
        background-color: #1da1f2;
        color: #fff;
    }
    .postbutton:hover {
        background-color: #0c8de4;
    }
    .postbutton:disabled {
        background-color: #b0d4f1;
        color: #fff;
        cursor: not-allowed;
    }
    .animate {
        width: 25px;
        padding: 10px;
        transition: background-color 0.4s, color 0.4s;
        color: #66757f;
    }

    .animate:hover {
        background-color: #e1f2fe;
        color: #1da1f2;
    }
</style>

