<template>
    <div class="wrapperCard">
        <!-- Display the post title -->
        <h2>{{ post.title }}</h2>
        <!-- Display the post content -->
        <p>{{ post.content }}</p>

        <!-- Container for action buttons for PostCard -->
        <div class="action-buttons">
            <button type="button">
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
}
</script>

<style scoped>

    h2 {
        text-align: center;
        margin: 10px 0 10px;
    }

    p {
        margin: 10px 0 25px;
    }

    .action-buttons {
        display: flex;
        justify-content: space-evenly;
    }

    button {
        border: none;
        background-color: white;
        cursor: pointer;
    }
     .icon {
        font-size: 1.2rem;
        margin: 10px 0;
        transition: .4s;
     }
     .icon:hover {
        transform: scale(1.2);
        transition: .4s;
     }
</style>
