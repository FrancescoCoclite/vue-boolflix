<template>
  <div>
    <form action=""><input type="text"><button type="button" class="btn btn-primary mx-3">Cerca</button></form>
    <div v-for="(element,index) in films" :key="index"> {{element[index].title}} {{element[index].original_title}} {{element[index].original_language}} {{element[index].vote_average}}</div>
  </div>
</template>

<script>
   import axios from 'axios';
export default {
  name: 'Main',
      data(){
        return{
            apiUrl : "https://api.themoviedb.org/3/movie/popular?api_key=e074c01e562b214f49b0d0b915aa74f1",
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
              this.films.push(picker.data.results);
              console.log(picker);
              
            })
        }
    }


}
</script>


<style scoped lang="scss">

</style>
