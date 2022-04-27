<template>
  <div class="mega_container">


    <div class="container" v-for="(element , index) in movies" :key="index">

      <div class="flip-box">

        <div class="flip-box-inner">

          <div class="flip-box-front">

            <div class="poster">
              <img :src="`https://image.tmdb.org/t/p/w500/${element.poster_path}`">
            </div>

          </div>

          <div class="flip-box-back">

            <p><span>Titolo: </span> {{ element.title }}</p>
            <p><span>Titolo originale: </span>{{ element.original_title }}</p>
            <div class="language">
              <p>Lingua: </p><img class="flag" :src="`https://countryflagsapi.com/svg/${element.original_language}`">
            </div>
            <div class="voto_container">
              <span>Voto: </span>
              <span class="stars_container">
                <span class="star" v-for="(element,index) in element.fullStars" :key="index"><img
                    src="../assets/img/full-star.png" alt=""></span>
                <span class="star" v-for="(element,index) in element.emptyStars" :key="index + 1"><img
                    src="../assets/img/empty-star.png" alt=""></span>
              </span>
            </div>

          </div>

        </div>
      </div>


    </div>


  </div>
</template>

<script>
  export default {
    name: 'MovieComp',
    props: {
      movies: Array
    },
    watch: {
      movies: function () {
        this.movies.forEach(element => {
          if (element.original_language == "en") {
            element.original_language = "us"
          }
        });
        this.movies.forEach(element => {
          element.vote_average = parseInt((element.vote_average) / 2)
          let fullStars = element.vote_average
          let emptyStars = 5 - fullStars
          element.fullStars = fullStars
          element.emptyStars = emptyStars
          console.log(emptyStars)
        });
      }
    },






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
    
    width: calc((100% / 5) - 20px);
    
    margin: 30px 10px;
    border-radius: 10px;



    .flag {
      height: 24px;
      width: 24px;
      border-radius: 50%;
      object-fit: cover;
      margin-left: 10px;
    }

    span {
      color: white;
      font-size: medium;


    }

    p {
      color: white;
      margin: auto 0;
    }

    .language {
      display: flex;
      align-items: center;
    }

    .star img {
      width: 100%;
    }

    .stars_container {
      display: flex;
      justify-content: center;
      margin: 0 10px;
    }

    .voto_container {
      display: flex;
      align-items: center;
    }
  }
  .poster{
    height: 100%;
  }
  .poster img {
    width: 100%;
    height: 100%;
    border-radius: 10px;
  }

  .flip-box {
    background-color: transparent;
    height: 300px;
    perspective: 1000px;
  
  }

  .flip-box-inner {
    position: relative;
    width: 100%;
    height: 100%;    
    transition: transform 0.8s;
    transform-style: preserve-3d;
    border-radius: 10px;
  }

  .flip-box:hover .flip-box-inner {
    transform: rotateY(180deg);
  }

  .flip-box-front,
  .flip-box-back {
    position: absolute;
    width: 100%;
    height: 100%;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
  }

  .flip-box-front {
    background-color: #bbb;
    border-radius: 10px;
  }

  .flip-box-back {
    background-color: #2e3a46;
    padding: 20px 10px;
    border-radius: 10px;
    transform: rotateY(180deg);

  }
</style>