<template>
<div>
  <form class="d-flex">
    <div> 
        <input v-model="cerca" type="text">
    </div>
    <div>
        <button @click="$emit('cercaFilm', cerca)" type="button" class="btn btn-primary mx-3">Cerca film</button>
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