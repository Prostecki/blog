<template>
    <aside :style="{ transform: 'translateX(' + (sidebarOpen ? '0px' : '-300px') + ')' }" class="sidebar"> 
        <button type="button" @click="closeSidebarHandler">X</button>
        <h1>{{ author }}</h1>
        <p>{{ message }}</p>
    </aside>
</template>

<script>
    export default {
        name: "SideBar",
        props: {
            sidebarOpen: Boolean,
            closeSidebar: Function,
        },
        methods: {
            closeSidebarHandler() {
                console.log('Closed');
                this.closeSidebar();
            }
        },
        data() {
            return {
                author: "Prostecki",
                message: "Hey everyone!",
            }
        },
    }
</script>

<style scoped>

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
    .sidebar-open {
        left: 0;
    }
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
    button:hover {
        background-color: red;
        color: white;
        transition: .4s;
    }

</style>