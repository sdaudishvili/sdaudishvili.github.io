<template>
    <div id="poster" v-if="movieObj!=''">
        <div id="imgCont">
            <img id="posterImg" v-bind:src="'https://image.tmdb.org/t/p/w500' + movieObj.poster_path">
        </div>
        <div id="overview">
            <h3>{{movieObj.title}}</h3>
            {{movieObj.vote_average}}<br>
            {{movieObj.vote_count}}<br>
            {{movieObj.release_date}}<br>
            {{movieObj.overview}}<br>
        </div>
        <!-- <div style="clear:both height: 0px overflow: hidden"></div> -->

    </div>
</template>

<script>
export default {
    name: 'Poster',
    props: [
        'movieObj'
    ],
    data() {
        return {
            imgBaseUrl: 'https://image.tmdb.org/t/p/w500'
        }
    },

    computed: {
        imgUrl() {
            return this.imgBaseUrl + this.movieObj.poster_path
        }
    },
}
</script>

<style>

@import '../assets/style/style.css';
</style>