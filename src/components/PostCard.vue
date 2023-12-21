<template>
    <div>
        <!-- Display the post title -->
        <h2>{{ post.title }}</h2>
        <!-- Display the post content -->
        <p>{{ post.content }}</p>
        <!-- Button with an icon (AkChatBubble) -->
        <button type="button">
            <!-- AkChatBubble icon component -->
            <AkChatBubble class="icon" />
        </button>
    </div>
</template>

<script>

// Import AkChatBubble component from @kalimahapps/vue-icons
import { AkChatBubble } from "@kalimahapps/vue-icons";

// Export the PostCard component
export default {
    components: {
        // Register AkChatBubble as a local component
        AkChatBubble,
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

</style>
