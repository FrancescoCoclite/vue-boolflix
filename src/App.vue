<template>
  <div id="app">
    <Search @cercaFilm="cercaFilm"/>
    <Main :ric="ricerca"/>

  </div>
</template>

<script>
import Main from './components/Main.vue'
import Search from '@/components/Search.vue'

export default {
  name: 'App',
    data(){
        return{
            ricerca : '',
        }
    },
     methods :{
        
      cercaFilm (str){
        console.log(str);
        this.ricerca = str

      }
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
