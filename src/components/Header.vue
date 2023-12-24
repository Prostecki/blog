<template>
    <div class="headbar">
        <button type="button">
            <AnOutlinedHome class="home" />
        </button>
        <h3>Contacts</h3>
        <h3>About</h3>
    </div>
</template>

<script>
    import { AnOutlinedHome } from "@kalimahapps/vue-icons";

    export default {
        name: "Header",
        components: {
            AnOutlinedHome
        }
    }
</script>

<style scoped>
    .headbar {
        width: 100%;
        margin: 20px 0;
        /* padding: 5px; */
        display: flex;
        justify-content: space-evenly;
        text-align: center;
        border-bottom: .5px solid black;
    }
    .headbar h3 {
        display: inline-block;
        border: .5px solid grey;
        padding: 5px;
        margin: 0 0 10px;
        color:  teal;
        transition: .4s;
        cursor: pointer;
    }
    h3:hover {
        color: white;
        transition: .4s;
    }
    button {
        width: 35px;
        padding: 5px;
        background: none;
        font-size: 25px;
        border: none;
        cursor: pointer;
    }
    button:hover {
        border-bottom: 2px solid black;
        box-sizing: border-box;
    }
</style>