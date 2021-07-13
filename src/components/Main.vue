<template>
  <div class="text-light bg-dark">
    <div class="container-lg">
      <div class="row">
        <div class="col-12">
          <h2 class="text-danger"> Films</h2>
          <div class="card d-inline-flex bg-transparent" style="width: 18rem;" v-for="(element,index) in films" :key="index">
            <div class="card-body" v-if=(element.title.toLowerCase().includes(ric.toLowerCase()))>
              <h5 class="card-title text-secondary">{{element.title}}</h5>
              <h6>{{element.original_title}}</h6>
              <p class="card-text">{{element.original_language}}</p>
              <p>{{element.vote_average}}</p>
            </div>
          </div>

        </div>
        <div class="col-12">
          <h2 class="text-danger">Serie tv</h2>
          <div class="card d-inline-flex bg-transparent" style="width: 18rem;" v-for="(element,index) in serie" :key="index">
            <div class="card-body" v-if=(element.name.toLowerCase().includes(ric.toLowerCase()))>
              <h5 class="card-title text-secondary">{{element.name}}</h5>
              <h6>{{element.original_title}}</h6>
              <p class="card-text" v-if="element.original_language.includes(bandiere.length)">{{element.original_language}}</p>
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
export default {
  name: 'Main',
      data(){
        return{
            bandiere: [
              '@/img/eng.png',
              '@/img/france.png',
              '@/img/giappone.png',
              '@/img/korea.png',
              '@/img/spain.png',
            ],
            apiUrl : "https://api.themoviedb.org/3/movie/popular?api_key=e074c01e562b214f49b0d0b915aa74f1",
            films : [],
            apiSerie : "https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=s",
            serie : [],

        }
    },
    props :{
      ric : String
    },
    components :{
      
    },
    created(){
        this.filmSelected()
        this.serieSelected()
    },
    methods :{
        filmSelected(){
            axios
            .get(this.apiUrl)
            .then(picker =>{
              this.films = picker.data.results;
              // console.log(picker);
              // console.log(this.films);
              
            })
        },
        serieSelected(){
            axios
            .get(this.apiSerie)
            .then(find =>{
              this.serie = find.data.results;
               console.log(find);
              
            })
        }
    }
}
</script>


<style scoped lang="scss">

</style>
