<template>
  <div class="sfondo text-light bg-dark">
    <div class="container-lg">
      <div class="row black">
        <div class="col-12"> 
          <h2 class="text-danger mb-5" id="film"> Films</h2>
          <div class="card d-inline-flex bg-transparent" style="width: 18rem;" v-for="(element,index) in films" :key="index">
           <img class="copertina position-relative" :src="'https://image.tmdb.org/t/p/w342' + element.poster_path" onerror="this.src='/img/img404.jpg'" alt="copertina-film">
            <div class="card-body position-absolute">
              <h5 class="card-title text-secondary">{{element.title}}</h5>
              <h6>{{element.original_title}}</h6>
              <p class="card-text">{{element.original_language}} <img class="flag" :src="'/img/'+element.original_language+'.png'" alt="bandiera"></p>
              <p>{{element.vote_average}} <star-rating :star-size=10 :read-only="true" :rating="Math.round((element.vote_average)/2)"></star-rating></p>
              <p class="overview">{{element.overview}}</p>
            </div>
          </div>

        </div>
        <div class="col-12">
          <h2 class="text-danger mt-5" id="serie">Serie tv</h2>
          <div class="card d-inline-flex bg-transparent" style="width: 18rem;" v-for="(element,index) in series" :key="index">
            <img class="copertina position-relative" :src="'https://image.tmdb.org/t/p/w342' + element.poster_path" onerror="this.src='/img/img404.jpg'" alt="copertina-serie">
            <div class="card-body position-absolute">
              <h5 class="card-title text-secondary">{{element.name}}</h5>
              <h6>{{element.original_title}}</h6>
              <p class="card-text">{{ element.original_language }}<img class="flag" :src="'/img/'+element.original_language+'.png'" alt="bandiera"></p>
              <p>{{element.vote_average}} <star-rating :star-size=15 :read-only="true" :rating="Math.round((element.vote_average)/2)"></star-rating></p>
              <p class="overview">{{element.overview}} </p>
            </div>
          </div>

        </div>
      </div>
    </div>

  </div>
</template>

<script>
import StarRating from 'vue-star-rating'
export default {
  name: 'Main',
      data(){
        return{
      }
    },
    props :{
        films : Array,
        series: Array,
    },
    components: {
    StarRating,
  }
}
</script>


<style scoped lang="scss">
  .flag{
    height: 30px;
    width: 30px;
  }
  .card:hover .copertina{
    z-index: -1;
  }
  .copertina{
    z-index: 999;
    height: 429px;
  }
  .card-body{
    background-color: black;
    height: 100%;
    width: 100%;
  }
  .sfondo{
    height: 100%;
  }
  .overview{
    font-size: 9px;
    &::selection{
      background-color: red;
    }
  }
  .card{
    margin: 15px;
  }
  
  
  
</style>
