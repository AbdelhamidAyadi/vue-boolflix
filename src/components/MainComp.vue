<template>
  <div>




    <div v-if="success">
      <MovieComp  :movies="movies" />
    </div>






    <div v-else class="loading">
      <div class="spinner-border" role="status">

      </div>
    </div>
  </div>
</template>

<script>
  import MovieComp from './MovieComp.vue'



  export default {
    name: 'MainComp',
    props: {
      movies: Array


    },
    components: {
      MovieComp,
    },
    data() {
      return {
        success: true
      }
    },
    created() {


    },

    watch: {

    }



  }
</script>

<style scoped lang="scss">

  .loading {
    .spinner-border {
      width: 5rem;
      height: 5rem;
    }

    color: white;
    position: absolute;
    left: 50%;
    top: 50%;

  }
</style>