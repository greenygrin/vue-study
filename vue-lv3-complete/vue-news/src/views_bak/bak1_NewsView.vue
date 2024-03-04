<template>
    <div>
        <!-- #1 <div v-for="user in users" v-bind:key="user.title">{{ user.title }}</div> -->
        <!-- #2 <div v-for="user in this.$store.state.news" v-bind:key="user.title">{{ user.title }}</div> -->
        <!-- #3 <div v-for="user in news" v-bind:key="user.title">{{ user.title }}</div> -->
        <!-- #5 <div v-for="user in newsItems" v-bind:key="user.title">{{ user.title }}</div> -->
        <!-- #6 <div v-for="user in fetchedNews" v-bind:key="user.title">{{ user.title }}</div> -->
        <!-- <p>
            -- #7 <a v-bind:href="item.url">{{ item.title }}</a> --
            <a :href="item.url">{{ item.title }}</a>
            <small>
                {{ item.time_ago }} by
                -- <router-link v-bind:to="'/user'+ item.user">{{ item.user }}</router-link> --
                <router-link v-bind:to="`/user/${item.user}`">{{ item.user }}</router-link>
            </small>
        </p> -->
        <ul class="news-list">
            <li v-for="item in fetchedNews" :key="item.title" class="post">
                <!-- 포인트 영역 -->
                <div class="points">
                    {{ item.points }}
                </div>
                <!-- 기타 정보 영역 -->
                <div>
                    <p class="news-title">
                        <a :href="item.url">
                            {{ item.title }}
                        </a>
                    </p>
                    <small class="link-text">
                        {{ item.time_ago }} by
                        <router-link v-bind:to="`/user/${item.user}`" class="link-text">
                            {{ item.user }}
                        </router-link>
                    </small>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
// #1
// import { fetchNewsList } from '../api/index.js'
// #4
// import { mapState } from 'vuex'
import { mapGetters } from 'vuex'

export default {
    // #1
    // data() {
    //     return {
    //         users: []
    //     }
    // },
    computed: {
        // #6
        ...mapGetters(['fetchedNews'])

        // #5
        // ...mapGetters({
        //     newsItems: 'fetchedNews'
        // })

        // #4
        // ...mapState({
        //     news: state => state.news
        // })

        // #3
        // news() {
        //     return this.$store.state.news;
        // }
    },
    created() {
        // #2
        this.$store.dispatch('FETCH_NEWS');

        // #1
        // fetchNewsList()
        //     .then(response => this.users = response.data)
        //     .catch(error => console.log(error));
    }
}
</script>

<style scoped>
.news-list {
    margin: 0;
    padding: 0;
}
.post {
    list-style: none;
    display: flex;
    align-items: center;
    border-bottom: 1px solid #eee;
}
.points {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 80px;
    height: 60px;
    color: #42b883;
}
.news-title {
    margin: 0;
}
.link-text {
    color: #828282;
}
</style>