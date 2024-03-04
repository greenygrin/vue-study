<template>
    <div id="root">
        <p>{{ originalPrice }}</p>
        <p>{{ doublePrice }}</p>
        <p>{{ triplePrice }}</p>
    </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
    computed: {
        // originalPrice() {
        //     return this.$store.getters.originalPric
        // },
        // doublePrice() {
        //     this.$store.getters.doublePrice
        // },
        // triplePrice() {
        //     this.$store.getters.triplePrice
        // }

        ...mapGetters(['originalPrice, doublePrice, triplePrice'])
    }
}
</script>

<style>

</style>