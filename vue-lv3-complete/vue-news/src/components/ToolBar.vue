<template>
    <div class="header">
        <router-link to="/news">News</router-link>
        <router-link to="/ask">Ask</router-link>
        <router-link to="/show">Show</router-link>
    </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.header {
    display: flex;
    padding: 8px;
    color: #fff;
    background-color: #42b883;
}
.header a {
    color: #fff;
}
.header a + a {
    margin-left:20px
}
.header .router-link-exact-active {
    color: #35495e;
}
</style>