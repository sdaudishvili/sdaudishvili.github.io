
<template>
  <div id="app">
    <div id="left">
      <img id="layer11" src="./assets/imgsrc/Layer11.png">
    </div>
    <div id="right">
      <Suggestions @movie="getObj"></Suggestions>
      
    </div>
    <Poster :movieObj='movie'></Poster>
    <div style="clear:both"></div>
    
    
    
  </div>
</template>

<script>
import Suggestions from './components/Suggestions.vue'
import Poster from './components/Poster.vue'


export default {
  name: 'app',
  components: {
    Suggestions,
    Poster
  },
  data(){
    return {
      movie: ''
    }
  },
  methods: {
    getObj(value){
      this.movie = value;
      console.log(this.movie)
    }
  }

  
}
</script>

<style>
  @import './assets/style/style.css';
</style>
