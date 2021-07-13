<template>
  <div id="app">
    <Search @cercaFilms="cercaFilms"/>
    <Main :films="films" :series="serie"/>

  </div>
</template>

<script>
import Main from './components/Main.vue'
import Search from '@/components/Search.vue'
import axios from 'axios';
export default {
  name: 'App',
    data(){
      return{
        apiURL: 'https://api.themoviedb.org/3/search/movie',
        apiURLserie: 'https://api.themoviedb.org/3/search/tv',
        apiKey: 'e074c01e562b214f49b0d0b915aa74f1',
        language: 'it-IT',
        films: [],
        serie: [],
    }
  },
 methods :{
        
    cercaFilms(str){
    axios
    .get(this.apiURL,{
      params:{
        api_key:this.apiKey,
        language: this.language,
        query:str
      }
    })
    .then(res =>{
      this.films= res.data.results;
      console.log(res);
    });
    axios
    .get(this.apiURLserie,{
      params:{
        api_key:this.apiKey,
        language: this.language,
        query:str
      }
    })
    .then(res =>{
      this.serie= res.data.results;
      console.log(res);
    });
    },
 
  },
  components: {
    Main,
    Search,
  }
}
</script>

<style lang="scss">
@import '@/style/general.scss';
@import '@/style/commons.scss';

</style>
