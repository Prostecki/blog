<template>
        <div :class="{ 'fade-out': isDeleting }" class="wrapperCard">
    
            <div class="user-avatar-container">
                <img class="avatar" :src="post.avatar">
            </div>
            
            <div class="post-content">
    
                <!-- Display the post title -->
                <h2>{{ post.name }}</h2>
    
                <!-- Display the post content -->
                <p>{{ post.content }}</p>
    
            </div>
    
            <!-- Container for action buttons for PostCard -->
            <div class="action-buttons">
                <button  @click="like" v-if="like" :class=" { 'like-button': likes } " type="button">
                    <AnOutlinedLike class="icon" />
                </button>
                <button type="button">
                    <AkArrowForwardThick class="icon" />
                </button>
                <!-- Button with an icon (AkChatBubble) -->
                <button type="button">
                    <!-- AkChatBubble icon component -->
                    <AkChatBubble class="icon" />
                </button>
                <button class="deletePost" type="button" @click="handleDelete">X</button>
            </div>
        </div>
</template>

<script>

// Import AkChatBubble component from @kalimahapps/vue-icons
import { AkChatBubble } from "@kalimahapps/vue-icons";
import { AkArrowForwardThick } from "@kalimahapps/vue-icons";
import { AnOutlinedLike } from "@kalimahapps/vue-icons";


// Export the PostCard component
export default {
    data() {
        return {
            isDeleting: false,
            likes: false,
        }
    },
    components: {
        // Register AkChatBubble as a local component
        AkChatBubble,
        AkArrowForwardThick,
        AnOutlinedLike
    },
    name: "PostCard", // Component name
    props: {
        post: {
            type: Object, // Expects the post prop to be an object
            required: true, // Post prop is required
        },
    },
    methods: {
        handleDelete() {
            try {
                this.isDeleting = true;
                setTimeout(() => {
                    // Emit the 'deletePost' event with the postId
                    this.$emit('deletePost', this.post.id);
                }, 500);
            } catch (error) {
                console.error('Something happened:', error);
            }
        },
        like() {
            this.likes = !this.likes;
        }
    },
}
</script>

<style scoped>
    .wrapperCard {
        position: relative;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    h2 {
        width: 100%;
        margin: 10px 0 10px;
    }
    p {
        margin: 10px 0 25px;
    }
    .action-buttons {
        width: 500px;
        display: flex;
        justify-content: space-evenly;
    }
    button {
        border: none;
        width: 25px;
        height: 25px;
        background-color: white;
        cursor: pointer;
        position: relative;
        overflow: hidden;
        border-radius: 50%;
    }
    button::before {
        content: '';
        position: absolute;
        width: 100%;
        height: 100%;
        background-color: #0c8de4;
        border-radius: 50%;
        top: 0;
        left: 0;
        transform: scale(0);
        transition: transform 0.2s ease;
    }
    button:hover::before {
        transform: scale(1);
    }
    .deletePost::before {
        content: 'X';
        font-size: 15px;
        color: white;
        position: absolute;
        width: 100%;
        height: 100%;
        margin: 5px 0;
        border-radius: 50%;
        transition: transform 0.2s ease;
    }
    .deletePost:hover::before {
        transform: scale(1);
    }
    .icon {
        font-size: 1.2rem;
        margin: 0;
        transition: .4s;
    }
    .icon:hover {
        transform: scale(1.2);
        transition: .4s;
    }
    .post-content {
        position: relative;
        display: flex;
        flex-wrap: wrap;
        width: 400px;
    }
    .user-avatar-container {
        width: 70px;
        position: absolute;
        top: 25px;
        left: 5px;
        margin: 0 0 0 10px;
        box-sizing: border-box;
    }
    .avatar {
        width: 100%;
        border-radius: 50%;
        background-position: center;
        background-size: cover;
    }
    button.like-button {
        background-color: red;
        color: white;
        transition: 0.2s ease;
    }
    .like-button .icon path {
        fill: red;
    }
</style>
