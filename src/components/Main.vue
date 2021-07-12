<template>
  <div>
    <div v-for="(element,index) in films" :key="index"> {{element.title}} {{element.original_title}} {{element.original_language}} {{element.vote_average}}</div>
  </div>
</template>

<script>
   import axios from 'axios';
export default {
  name: 'Main',
      data(){
        return{
            apiUrl : "https://api.themoviedb.org/3/movie/550?api_key=e074c01e562b214f49b0d0b915aa74f1",
            films : [],
            
        }
    },
    created(){
        this.filmSelected()
    },
    methods :{
        filmSelected(){
            axios
            .get(this.apiUrl)
            .then(picker =>{
              this.films.push(picker.data);
              console.log(picker);
            })
        }
    }


}
</script>


<style scoped lang="scss">

</style>
