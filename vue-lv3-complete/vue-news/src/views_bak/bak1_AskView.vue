<template>
    <div>
        <!-- <div v-for="item in ask" v-bind:key="item.title">{{ item.title }}</div> -->
        <!-- <div v-for="item in this.$store.state.ask" v-bind:key="item.title">{{ item.title }}</div> -->
        <p v-for="item in this.$store.state.ask" :key="item.title">
            <!-- <a :href="item.url">{{ item.title }}</a> -->
            <!-- <router-link v-bind:to="`item/${item.id}`">{{ item.title }}</router-link> -->
            <router-link :to="`item/${item.id}`">{{ item.title }}</router-link>
            <small>{{ item.time_ago }} by {{ item.user }}</small>
        </p>
    </div>
</template>

<script>
// import { fetchAskList } from '../api/index.js'

export default {
    // data() {
    //     return {
    //         ask: []
    //     }
    // },
    created() {
        this.$store.dispatch('FETCH_ASK');

        // fetchAskList()
        //     .then(response => this.ask = response.data)
        //     .catch(error => console.log(error));
    }
}
</script>

<style>

</style>