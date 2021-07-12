<template>
<div class="bg-dark" >
  <form class="d-flex">
    <div> 
        <input v-model="cerca" type="text">
    </div>
    <div>
        <button @click="$emit('cercaFilm', cerca)" type="button" class="btn btn-danger mx-3">Cerca film</button>
    </div>
   </form>
</div>

</template>

<script>
export default {
    name: 'Search',
    data(){
        return{
            cerca : ''
        }
    }
}
</script>

<style>

</style>