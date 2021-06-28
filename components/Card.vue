<template>
    <div class="num">
        <h3>{{username}}</h3>
        <p>{{company}}</p>
        <p>{{adresse}}</p>
        <p>{{phone}}</p>
    </div>
</template>

<script>
    export default {
        props: ["username","company","adresse","phone"],
        data() {
        return {};
        },
        
    }
</script>

<style lang="scss" scoped>
    .num{
        background-color: white;
        width: 220px;
        height: 200px;
        color: purple;
        font-weight: 500;
        display: flex; 
        flex-direction: column;
        row-gap: 8px;
        padding: 1em;
        text-align: center;
    }
</style>