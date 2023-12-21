<template>
    <div class="headbar">
        <h3>Home</h3>
        <h3>Contacts</h3>
        <h3>About</h3>
    </div>
</template>

<script>
    export default {
        name: "Header"
    }
</script>

<style scoped>
    .headbar {
        margin: 20px 0;
        /* padding: 5px; */
        display: flex;
        justify-content: space-evenly;
        text-align: center;
        border-bottom: .5px solid black;
    }
    .headbar h3 {
        padding: 5px;
        margin: 0 0 10px;
        color:  teal;
    }
</style>