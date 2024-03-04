<template>
    <div>
        <!-- <div v-for="item in show" v-bind:key="item.title">{{ item.title }}</div> -->
        <!-- <div v-for="item in this.$store.state.show" v-bind:key="item.title">{{ item.title }}</div> -->
        <p v-for="item in this.$store.state.show" :key="item.title">
            <a :href="item.url">{{ item.title }}</a>
            <small>{{ item.time_ago }} by {{ item.user }}</small>
        </p>
    </div>
</template>

<script>
// import { fetchShowList } from '../api/index.js'

export default {
    // data() {
    //     return {
    //         show: []
    //     }
    // },
    created() {
        this.$store.dispatch('FETCH_SHOW');

        // fetchShowList()
        //     .then(response => this.show = response.data)
        //     .catch(error => console.log(error));
    }
}
</script>

<style>

</style>