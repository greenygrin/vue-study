<template>
    <div><!-- 최상위 html은 하나만 사용해야함 -->
        <!-- <app-header v-bind:프롭스 속성 이름="상위 컴포넌트의 데이터 이름"></app-header> -->
        <app-header
            v-bind:propsdata="str"
            v-on:renew="renewStr"></app-header>
    </div>
</template>

<script>
// var AppHeader = {
//     template: '<header><h1>Header</h1></header>'
// }

// new Vue({
//     data: {
//         str: 'hi'
//     }
// })

import AppHeader from './components/AppHeader.vue';

export default {
    data: function() {
        return {
            str: 'Header'
        }
    },
    components: {
        'app-header': AppHeader
    },
    methods: {
        renewStr: function() {
            this.str = 'hi';
        }
    }
}
</script>

<style>

</style>