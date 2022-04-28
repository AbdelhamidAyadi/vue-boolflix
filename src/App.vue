<template>
  <div class="body">
    <header>
      <HeaderComp @search="searchFunction" />
    </header>
    <main v-if="success">
      <MainComp :movies="movies" :series="series" />

    </main>
    <div v-else class="greetings">
      <div class="greetings_container">
        <h1>See what's next.</h1>
        <p>Movie and TV shows Database </p>
      </div>
    </div>
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
        series: [],
        search: "",
        success: false
      }

    },
    created() {


    },
    watch: {
      search: function () {
        let self = this
        self.success = false
        axios.get(
            `https://api.themoviedb.org/3/search/movie?api_key=4c0444add8d6d33251130b482d242683&language=en-US&page=1&query=${this.search}`,
          )
          .then(function (response) {
            self.movies = response.data.results
            console.log(self.movies)
          })
        axios.get(
            `https://api.themoviedb.org/3/search/tv?api_key=4c0444add8d6d33251130b482d242683&language=en-US&page=1&query=${this.search}`,
          )
          .then(function (response) {
            self.series = response.data.results
            console.log(self.series)
          })

        self.success = true


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
    background-color: #262626;
    min-height: 100vh;

  }

  .body {
    min-height: 100vh;
    position: relative;
  }

  .greetings {
    color: white;
    padding-top: 80px;
    background-image: url('https://xbox-store-checker.com/assets/upload/game/2019/02/optimize/9wzdncrfj3tj-background.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;

    .greetings_container {
      h1{
        font-size: 5rem;
      }
    }

  }
</style>