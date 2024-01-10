<template>
    <div class="comment-item">
      <h3>{{ comment.author }}</h3>
      <p>{{ comment.text }}</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "CommentItem",
    props: {
      comment: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  /* Стили для CommentItem могут быть добавлены здесь */
  </style>
