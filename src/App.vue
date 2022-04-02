<template>
  <div id="app">
    <IndexHeader @search="searchAll" />
    <IndexMain
    :filmsArray ="matchedFilms"
    
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
      matchedFilms:null,
      matchedSeries:null,
    }
  },
  methods:{
    getFilms(queryString){
      const filmsUrl = `https://api.themoviedb.org/3/search/movie?api_key=276a8d5ac6ab05e1c8488deebdcb905d&language=it-It&query=${queryString}&page=1`
      return axios.get(filmsUrl) 
    },
    getSeries(queryString){
      const seriesUrl = `https://api.themoviedb.org/3/search/tv?api_key=276a8d5ac6ab05e1c8488deebdcb905d&language=it_IT&query=${queryString}`
      return axios.get(seriesUrl)
    },



    searchAll(queryString){
      const self=this
      
      axios
      .all([this.getFilms(queryString),this.getSeries(queryString)])
      
      .then(function (responsefilms,responseSeries){
        const resultFilms = responsefilms.data.results;
        const resultSeries = responseSeries.data.results;
        self.matchedFilms = resultFilms;
        self.matchedSeries = resultSeries
        console.log(self.matchedFilms)
        console.warn(self.matchedSeries)
      })

      
    },
    
  },
}
</script>

<style lang="scss" scoped>

</style>
