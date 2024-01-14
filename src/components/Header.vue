<template>
    <div class="headbar">
        <button type="button">
            <AnOutlinedHome class="home" />
        </button>
        <h3>Contacts</h3>
        <h3 @click="openSideBar">About</h3>
        <h3 @click="openProfileMenu">Profile</h3>
    </div>
</template>

<script>

    import { AnOutlinedHome } from "@kalimahapps/vue-icons";

    export default {
        name: "Header",
        components: {
            AnOutlinedHome
        },
        data() {
          return {
            currentUser: {
              // Здесь данные о текущем пользователе
            },
          }
        },
        methods: {
            openSideBar() {
              this.$emit('open-sidebar');
            },
            openProfileMenu() {
              this.$emit('open-profileMenu')
            },
            openProfileDialog() {
              this.isProfileDialogVisible = true;
            },
            closeProfileDialog() {
              this.isProfileDialogVisible = false;
            },
        }
    }
</script>

<style scoped>
  .headbar {
    width: 100%;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    padding: 12px 20px;
    background-color: #fff;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  .headbar h3 {
    margin: 0;
    padding: 5px;
    font-size: 1.2rem;
    color: #1da1f2;
    cursor: pointer;
    transition: color 0.4s;
  }
  .headbar h3:hover {
    color: #0c8de4;
    border: 1px solid #1da1f2;
    border-radius: 12px;
  }
  button {
    width: 35px;
    height: 35px;
    padding: 0;
    background: none;
    font-size: 20px;
    border: none;
    cursor: pointer;
    transition: border-bottom 0.4s;
  }
  button:hover {
    border-bottom: 2px solid #1da1f2;
    box-sizing: border-box;
  }
  .home {
    color: #1da1f2;
    transition: color 0.4s;
  }
  .home:hover {
    color: #0c8de4;
  }
</style>
