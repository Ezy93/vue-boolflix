<template>
  <div id="app">
    <IndexHeader @search="searchFilms"/>
    <IndexMain/>
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
      
    }
  },
  methods:{
    searchFilms(queryString){
      const self = this
      
      axios
      .get(`https://api.themoviedb.org/3/search/movie?api_key=276a8d5ac6ab05e1c8488deebdcb905d&language=en-US&query=${queryString}&page=1`)
      .then(function (response){
        const result = response.data.results;
        self.matchedFilms = result;
        console.log(self.matchedFilms)
      })

      
    }
  },
}
</script>

<style lang="scss" scoped>

</style>
