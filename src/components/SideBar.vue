<template>
    <!-- Sidebar component -->
    <aside :style="{ transform: 'translateX(' + (sidebarOpen ? '0px' : '-300px') + ')' }" class="sidebar"> 
        <!-- Close button for the sidebar -->
        <button type="button" @click="closeSidebarHandler">X</button>
        <!-- Author's name -->
        <h1>{{ author }}</h1>
        <!-- Message in the sidebar -->
        <p>{{ message }}</p>
    </aside>
</template>

<script>
    export default {
        // Component name
        name: "SideBar",
        // Props for receiving data from the parent component
        props: {
            sidebarOpen: Boolean,   // Boolean prop indicating if the sidebar is open
            closeSidebar: Function, // Function prop to close the sidebar
        },
        // Methods for handling actions in the component
        methods: {
            // Method to handle closing the sidebar
            closeSidebarHandler() {
                console.log('Closed');  // Log message when sidebar is closed
                this.closeSidebar();     // Call the provided closeSidebar function
            }
        },
        // Data properties for storing component-specific data
        data() {
            return {
                author: "Prostecki",    // Author's name
                message: "Hey everyone!", // Message in the sidebar
            }
        },
    }
</script>

<style scoped>
  /* Styling for the sidebar */
  .sidebar {
    text-align: left;
    width: 200px;
    height: 100%;
    background-color: #fff;
    color: #14171a;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    position: fixed;
    z-index: 5;
    top: 0;
    border-right: 1px solid #e1e8ed;
    transition: left 0.4s ease;
  }
  .sidebar-open {
    left: 0;
  }
  /* Styling for the close button */
  button {
    position: absolute;
    top: 10px;
    right: 10px;
    width: 30px;
    height: 30px;
    font-size: 16px;
    font-weight: bold;
    background: none;
    border: none;
    cursor: pointer;
    transition: background-color 0.4s, color 0.4s;
  }
  /* Styling for the close button on hover */
  button:hover {
    background-color: #e1e8ed; /* Twitter's button hover color */
    color: #1da1f2; /* Twitter's blue color */
  }
</style>

