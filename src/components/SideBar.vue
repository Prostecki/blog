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
        text-align: center;
        width: 250px;
        height: 400px;
        background-color: #444;
        color: white;
        padding: 20px;
        border-radius: 0 12px 12px 0;
        position: fixed;
        z-index: 5;
        top: 0;
        transition: -webkit-transform 0.4s ease;
        transition: transform 0.4s ease;
    }
    /* Styling for the open state of the sidebar */
    .sidebar-open {
        left: 0;
    }
    /* Styling for the close button */
    button {
        position: absolute;
        border-radius: 0 12px 0 0;
        top: 0;
        right: 0;
        width: 25px;
        font-size: 15px;
        font-weight: bolder;
        padding: 5px;
        background: none;
        border: .5px solid grey;
        cursor: pointer;
        transition: .4s;
    }
    /* Styling for the close button on hover */
    button:hover {
        background-color: red;
        color: white;
        transition: .4s;
    }
</style>
