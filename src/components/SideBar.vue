<template>
    <aside :style="{ left: sidebarPosition }" class="slidebar"> 
        <button type="button">X</button>
        <h1>{{ author }}</h1>
        <p>{{ message }}</p>
    </aside>
</template>

<script>
    export default {
        name: "SideBar",
        data() {
            return {
                author: "Prostecki",
                message: "Hey everyone!",
                sidebarPosition: String,
            }
        },
        methods: {
            toggleSideBar() {
                this.sidebarPosition = this.sidebarPosition === '0px' ? '-250px' : '0px';
            }
        }
    }
</script>

<style scoped>

    .slidebar {
        width: 250px;
        height: 100vh;
        background-color: #444;
        color: white;
        padding: 20px;
        position: fixed;
        top: 0;
        transition: left 0.3s ease;
    }
    button {
        position: absolute;
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