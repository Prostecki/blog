<template>
    <div>
        <h2>{{ post.title }}</h2>
        <p>{{ post.content }}</p>
        <button type="button">
            <AkChatBubble class="icon" />
        </button>
    </div>
</template>

<script>
import { AkChatBubble } from "@kalimahapps/vue-icons";
    export default {
        components: {
            AkChatBubble,
        },
        name: "PostCard",
        props: {
            post: {
                type: Object,
                required: true,
            },
        }
    }
</script>

<style scoped>

</style>