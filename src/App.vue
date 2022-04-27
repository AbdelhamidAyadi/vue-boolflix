<template>
  <div class="body">
    <header>
      <HeaderComp @search="searchFunction" />
    </header>
    <main>
      <MainComp :movies="movies" />
     
    </main>
  </div>
</template>

<script>
  import HeaderComp from './components/HeaderComp.vue'
  import MainComp from './components/MainComp.vue'
  import axios from 'axios'
  export default {
    name: 'App',
    components: {
      HeaderComp,
      MainComp
    },
    data() {
      return {
        movies: [],
        search: ""
      }

    },
    created() {


    },
    watch: {
      search: function () {
        let self = this
        
        axios.get(
            `https://api.themoviedb.org/3/search/movie?api_key=4c0444add8d6d33251130b482d242683&language=en-US&page=1&query=${this.search}`,
            )
          .then(function (response) {
            self.movies = response.data.results
            console.log(self.movies)
          })
           
         
      }
    },
    methods: {
      searchFunction(searchedText) {
        this.search = searchedText
      }
    }
  }
</script>

<style lang="scss">
  @import "bootstrap/dist/css/bootstrap.min.css";


  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  header {
    position: fixed;
    z-index: 1;
    width: 100%;

  }

  main {
    padding-top: 80px;
    
  }

  .body {
    background-color: #262626;
    min-height: 100vh;
    position: relative;
  }
</style>