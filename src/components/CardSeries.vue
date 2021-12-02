<template>
  <div class="card">
      <div class="card-inner">
        <div class="front">
          <img class="poster" :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" :alt="`Locandina ${result.name}`">
        </div>
        <div class="back">
          <ul>
            <li>
              <strong>Titolo originale: </strong>
              <p>{{result.original_name}}</p>
            </li>
            <li>
              <strong>Lingua originale: </strong>
              <img class="language-flag" 
                src="../assets/img/it.png" alt="bandiera italiana"
                v-if="result.original_language == 'it'"
              >
              <img class="language-flag" 
                src="../assets/img/en.png" alt="bandiera regno unito"
                v-else-if="result.original_language == 'en'"
              >
              <p v-else>{{result.original_language}}</p>
            <li>
              <strong>Titolo: </strong>
              <p>{{result.name}}</p>
            </li>
            <li>
              <strong>Data di Uscita: </strong>
              <p>{{result.first_air_date.split('-').reverse().join('/')}}</p>
            </li>
            <li>
              <strong>Valutazione: </strong>
              <p>{{result.vote_average}}</p>
            </li>
            <li>
              <strong>Descrizione: </strong>
              <p v-if=" result.overview !== '' ">
                {{result.overview}}
              </p>
              <p v-else>N/A</p>
            </li>
            
          </ul>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'CardSeries',
  props: {
    result: Object
  }
}
</script>

<style lang="scss">
  // .card {
  //   width: calc(100% / 4 - 40px);
  //   margin: 20px;
  //   padding: 20px;
  //   // background-color: tomato;
  //   min-height: 400px;
  //   font-family: Arial, Helvetica, sans-serif;
  //   // overflow: auto;

  //   perspective: 1000px;
  //     .card-inner {
  //       position: relative;
  //       width: 100%;
  //       height: 100%;
  //       text-align: center;
  //       transition: transform 0.8s;
  //       transform-style: preserve-3d;
  //       .front img {
  //         width: 100%;
  //         height: 100%;
  //         object-fit: cover;
  //       }
  //     }
  //   &:hover .card-inner {
  //     transform: rotateY(180deg);
  //   } 
  //     .front, .back {
  //       position: absolute;
  //       width: 100%;
  //       height: 100%;
  //       backface-visibility: hidden;
  //     } 
  //     .back {
  //       background-color: lightgrey;
  //       transform: rotateY(180deg);
  //     }
  //   ul {
  //     padding: 30px 0;
  //     li {
  //       padding-bottom: 20px;
  //       img.language-flag {
  //         width: 30px;
  //         vertical-align: middle;
  //       }
  //       p {
  //         display: inline-block;
  //       }
  //     }
  //   }
  // }
</style>