<template>
    
    <div class="a">
        <input autocomplete="off" v-model="movieName" v-on:keyup="getInput()" type="text" id="search-field" placeholder="Enter the movie name...">
        <table v-if="movieName != ''">
            <tbody v-bind:key="info.results.id" v-for="movie in info.results">
                <tr class="autocomplete-result" v-if="checkTitle(movie.title)" @mousedown="getMovie(movie)">
                    <td>{{movie.title}}</td>
                </tr>
            </tbody>
        </table>
    </div>

</template>

<script>


export default {
    name: 'Suggestions',
    props: [

    ],
    data(){
        return {
            
            movieName: '',
            baseUrl: "https://api.themoviedb.org/3/search/movie?api_key=9e2168f32202773e09b57af0e9187563&query=",
            info: '',
            selected: false,
        }
    },
    computed: {
        apiUrl() {
            return this.baseUrl + this.movieName
        }
    },
    methods: {
        getInput: function(){
            if(this.movieName == ''){
                console.log("waiting for user input");
                this.selected = false;
            }else{
                if(!this.selected){
                    this.axios.get(this.apiUrl)
                    .then((response) => {
                        this.info = response.data;
                    })
                }
            }
        },

        checkTitle: function(title){
            if(this.movieName.toLowerCase() == title.substr(0,this.movieName.length).toLowerCase()){
                // console.log(title);
                return true;
            }
            return false;
        },
        getMovie: function(movie){
            this.movieName = movie.title;
            this.info = '';
            this.selected = true;
            this.$emit('movie', movie)
        }
        
 
    }

}
</script>


<style>


@import '../assets/style/style.css';
</style>