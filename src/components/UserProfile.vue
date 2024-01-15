<template>
    <div :class="{ 'user-profile': true, 'closed': !profileCardOpen }">
      <div class="dialog-content">
        <button @click="closeDialog" class="close-button">X</button>
        <div class="profile-info">
          <img :src="user.avatar" alt="Profile Picture" class="avatar" />
          <h2>{{ user.name }}</h2>
          <p>{{ user.bio }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      profileCardOpen: Boolean,
      closeProfileCard: Function,
    },
    data() {
      return {
        // Random info about profile 
        user: {
          name: "John Doe",
          bio: "Web Developer",
          avatar: "https://placekitten.com/200/200", // Random link for icon
        },
      };
    },
    methods: {
      closeDialog() {
        this.closeProfileCard();
        this.$emit("user-data", this.user);
      },
      emitUserData() {
        this.$emit('user-data', this.user);
      }
    },
  };
  </script>
  
  <style scoped>
  .user-profile {
    position: fixed;
    top: 0;
    right: 0;
    width: 300px;
    height: 100%;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 9;
    transition: right 0.5s ease;
  }
  
  .closed {
    right: -700px;
  }
  
  .dialog-content {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    position: relative;
  }
  
  .close-button {
    position: absolute;
    top: 10px;
    right: 10px;
    font-size: 16px;
    font-weight: bold;
    background: none;
    border: none;
    cursor: pointer;
    transition: background-color 0.4s, color 0.4s;
  }
  
  .close-button:hover {
    background-color: #e1e8ed;
    color: #1da1f2;
  }
  
  .profile-info {
    text-align: center;
  }
  
  .avatar {
    width: 100px;
    height: 100px;
    border-radius: 50%;
    margin-bottom: 10px;
  }
  </style>
  