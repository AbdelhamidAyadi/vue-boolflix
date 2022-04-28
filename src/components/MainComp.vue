<template>
  <div>

    <div >
      <MovieComp  :movies="movies" :series="series" />
    </div>


    
  </div>
</template>

<script>
  import MovieComp from './MovieComp.vue'



  export default {
    name: 'MainComp',
    props: {
      movies: Array,
      series:Array


    },
    components: {
      MovieComp,
    },
    data() {
      return {
        
      }
    },
    created() {


    },

    watch: {

    }



  }
</script>

<style scoped lang="scss">

 
</style>