<template>
  <div>
    <div class="container-lg">
      <div class="row">
        <div class="col-12 mb-5 ">
          <Search/>
        </div>
        <div class="col-12">

          <div class="card d-inline-flex mx-3 mt-2" style="width: 18rem;" v-for="(element,index) in films" :key="index">
            <div class="card-body">
              <h5 class="card-title">{{element.title}}</h5>
              <h6>{{element.original_title}}</h6>
              <p class="card-text">{{element.original_language}}</p>
              <p>{{element.vote_average}}</p>
            </div>
          </div>

        </div>
      </div>
    </div>

  </div>
</template>

<script>

   import axios from 'axios';
   import Search from '../components/Search.vue'
export default {
  name: 'Main',
      data(){
        return{
            apiUrl : "https://api.themoviedb.org/3/movie/popular?api_key=e074c01e562b214f49b0d0b915aa74f1",
            films : [],
            
        }
    },
    components :{
      Search,
    },
    created(){
        this.filmSelected()
    },
    methods :{
        filmSelected(){
            axios
            .get(this.apiUrl)
            .then(picker =>{
              this.films = picker.data.results;
              console.log(picker);
              console.log(this.films);
              
            })
        }
    }
}
</script>


<style scoped lang="scss">

</style>
