<template>
  <div class="card">
      <div class="card-inner">
        <div class="front">
          <img class="poster" :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" :alt="`Locandina ${result.title}`">
        </div>
        <div class="back">
          <ul>
            <li>
              <strong>Titolo originale: </strong>
              <p>{{result.original_title}}</p>
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
              <p>{{result.title}}</p>
            </li>
            <li>
              <strong>Data di Uscita: </strong>
              <p>{{result.release_date.split('-').reverse().join('/')}}</p>
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
  name: 'Card',
  props: {
    result: Object
  }
}
</script>

<style lang="scss">
  .card {
    width: calc(100% / 5 - 40px);
    margin: 20px;
    min-height: 400px;
    font-family: Arial, Helvetica, sans-serif;
    box-shadow: ;

    perspective: 1000px;
      .card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        // text-align: center;
        transition: transform 0.8s;
        transform-style: preserve-3d;
        outline: 1px solid white;
        .front {
          background-color: tomato;
          img {
          width: 100%;  
          max-width: initial;
          height: 100%;
          max-height: initial;
        }
        }
      }
    &:hover .card-inner {
      transform: rotateY(180deg);
    } 
      .front, .back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
      } 
      .back {
        padding-left: 7px;
        background-color: black;
        color: white;
        transform: rotateY(180deg);
      }
    // overflow: auto;
    ul {
      padding: 10px 0;
      li {
        padding-bottom: 20px;
        img.language-flag {
          width: 30px;
          vertical-align: middle;
        }
        p {
          display: inline-block;
        }
      }
    }
  }
</style>
