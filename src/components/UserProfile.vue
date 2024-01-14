<template>
    <div v-if="isVisible" class="dialog-overlay">
      <div class="dialog-content">
        <button @click="closeDialog" class="close-button">X</button>
        <ProfileCard :user="user" />
      </div>
    </div>
  </template>
  
  <script>
  import ProfileCard from "@/components/ProfileCard.vue";
  
  export default {
    props: {
      isVisible: {
        type: Boolean,
        required: true,
      },
      user: {
        type: Object,
        required: true,
      },
    },
    components: {
      ProfileCard,
    },
    methods: {
      closeDialog() {
        this.$emit("close");
      },
    },
  };
  </script>
  
  <style scoped>
  .dialog-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .dialog-content {
    background: white;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    position: relative;
  }
  
  .close-button {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 16px;
    color: #333;
  }
  </style>
  