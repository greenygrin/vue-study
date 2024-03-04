<template>
    <div id="app">
        <!-- <ToolBar></ToolBar> -- Strongly Recommended : vue 스타일 가이드에서 추천하는 스타일 -->
        <tool-bar></tool-bar><!-- Essential : vscode 자동완성을 사용하기 위함 -->
        <transition name="page">
            <router-view></router-view>
        </transition>
        <spinner :loading="loadingStatus"></spinner>
    </div>
</template>

<script>
import ToolBar from './components/ToolBar.vue'
import Spinner from './components/Spinner.vue'
import bus from './utils/bus.js'

export default {
    components: {
        ToolBar,
        Spinner
    },
    data() {
        return {
            loadingStatus: false
        }
    },
    methods: {
        startSpinner() {
            this.loadingStatus = true;
        },
        endSpinner() {
            this.loadingStatus = false;
        }
    },
    created() {
        bus.$on('start:spinner', this.startSpinner);
        bus.$on('end:spinner', this.endSpinner);
    },
    beforeDestory() {
        bus.$off('start:spinner', this.startSpinner);
        bus.$off('end:spinner', this.endSpinner);
    }
}
</script>

<style>
body {
    padding: 0;
    margin: 0;
}
a {
    color: #34495e;
    text-decoration: none;
}
a:hover {
    color: #42b842;
    text-decoration: underline;
}
a.router-link-exact-active {
    text-decoration: underline;
}

/* Router Transition */
.page-enter-active, .page-leave-active {
  transition: opacity .5s;
}
.page-enter, .page-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
