<template>
  <div class="sfondo text-light bg-dark">
    <div class="container-lg">
      <div class="row">
        <div class="col-12"> 
          <h2 class="text-danger" id="film"> Films</h2>
          <div class="card d-inline-flex bg-transparent" style="width: 18rem;" v-for="(element,index) in films" :key="index">
           <img class="copertina position-relative" :src="'https://image.tmdb.org/t/p/w342' + element.poster_path" alt="copertina-film">
            <div class="card-body position-absolute">
              <h5 class="card-title text-secondary">{{element.title}}</h5>
              <h6 d-none>{{element.original_title}}</h6>
              <p class="card-text">{{element.original_language}} <img class="flag" :src="'/img/'+element.original_language+'.png'" alt="bandiera"></p>
              <p>{{element.vote_average}}</p>
            </div>
          </div>

        </div>
        <div class="col-12">
          <h2 class="text-danger" id="serie">Serie tv</h2>
          <div class="card d-inline-flex bg-transparent" style="width: 18rem;" v-for="(element,index) in series" :key="index">
            <img class="copertina position-relative" :src="'https://image.tmdb.org/t/p/w342' + element.poster_path" alt="copertina-serie">
            <div class="card-body position-absolute">
              <h5 class="card-title text-secondary">{{element.name}}</h5>
              <h6>{{element.original_title}}</h6>
              <p class="card-text">{{ element.original_language }}<img class="flag" :src="'/img/'+element.original_language+'.png'" alt="bandiera"></p>
              <p>{{element.vote_average}}</p>
            </div>
          </div>

        </div>
      </div>
    </div>

  </div>
</template>

<script>

   
export default {
  name: 'Main',
      data(){
        return{
      }
    },
    props :{
        films : Array,
        series: Array,
    }
}
</script>


<style scoped lang="scss">
  .flag{
    height: 30px;
    width: 30px;
  }
  .copertina{
    z-index: 999;
    &:active{
      z-index: 00;
    }
  }
  .card-body{
    background-color: black;
    height: 100%;
    width: 100%;
  }
  .sfondo{
    height: 100%;
  }
  
  
  
  
</style>
