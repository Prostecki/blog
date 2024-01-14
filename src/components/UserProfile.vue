<template>
    <div :style="{ transform: 'translateX(' + (profileCardOpen ? '0px' : '-700px') + ')' }" class="userProfile">
      <div class="dialog-content">
        <button @click="closeDialog" class="close-button">X</button>
      </div>
    </div>
  </template>
  
  <script>
  
  export default {

    props: {
        profileCardOpen: Boolean,
        closeProfileCard: Function,
    },
    methods: {
      closeDialog() {
        this.closeProfileCard();
      },
    },
  }
  </script>
  
  <style scoped>

.userProfile {
  position: fixed;
  top: 0;
  right: -700px;
  width: 300px;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5); /* Полупрозрачный черный фон */
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9; /* Поверх других элементов */
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

  </style>
  