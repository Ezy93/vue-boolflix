<template>
  <div id="app">
    <IndexHeader @search="searchFilms" />
    <IndexMain
    :filmsArray ="matchedFilms"
    :seriesArray="matchedSeries"
    
    />
  </div>
</template>

<script>
import IndexHeader from './components/IndexHeader.vue';
import IndexMain from './components/IndexMain.vue';
import './scss/style.scss';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    IndexHeader,
    IndexMain,
  },
  data: function(){
    return{
      /* ricordarsi che facendo cosi appena si apre la pagina dice subito che la ricerca non ha prodotto risultati e se la metto a null mi da un errore */
      matchedFilms:[],
      matchedSeries:[],
    }
  },
  methods:{
    


    
    searchFilms(queryString){
      const self=this
      
      axios
      .get(`https://api.themoviedb.org/3/search/movie?api_key=276a8d5ac6ab05e1c8488deebdcb905d&language=it-It&query=${queryString}`)
      
      .then(function (response){
        const result = response.data.results;
        self.matchedFilms = result;
        console.log(self.matchedFilms)
        
      })

      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=276a8d5ac6ab05e1c8488deebdcb905d&language=it_IT&query=${queryString}`)
      .then(function(response){
        const result = response.data.results;
        self.matchedSeries = result;
        console.warn(self.matchedSeries)
      })

      
    },
    /* searchSeries(queryString){
      const self=this
      axios
      .get(`https://api.themoviedb.org/3/search/tv?api_key=276a8d5ac6ab05e1c8488deebdcb905d&language=it_IT&query=${queryString}`)
      
      .then(function (response){
        const result = response.data.results;
        self.matchedSeries = result;
        console.warn(self.matchedSeries)
      })
    } */
  },
}
</script>

<style lang="scss" scoped>

</style>
