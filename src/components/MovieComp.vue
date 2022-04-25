<template>
  <div class="mega_container">
    <div v-for="(element , index) in movies" :key="index" class="container">
      <p><span>Titolo: </span> {{ element.title }}</p>
      <p><span>Titolo originale: </span>{{ element.original_title }}</p>
      <img :src="`https://countryflagsapi.com/svg/${element.original_language}`">
      <p><span>Voto: </span>{{ element.vote_average }}</p>
    </div>
    
  </div>
</template>

<script>
  export default {
    name: 'SongComp',
    props: {
      movies: Array
    },
    watch:{
      movies:function() {
       this.movies.forEach(element => {
          if (element.original_language == "en") {
          element.original_language = "us"
        }
       });
      }
    }
    
    

  }
</script>

<style scoped lang="scss">
.mega_container {
    display: flex;
    justify-content: center;

    flex-wrap: wrap;
    width: 80%;
    margin: 0 auto;
  }
  .container {
    display: inline-block;
    background-color: #2e3a46;
    width: calc((100% / 5) - 20px);
    padding: 20px 10px;
    margin: 30px 10px;
    
    border-radius: 10px;
    

    img {
      width: 80%;
    }

    span {
      color: white;
      font-size: medium;

    
    }

    p {
      color: white;
    }
  }
</style>