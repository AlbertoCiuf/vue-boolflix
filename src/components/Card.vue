<template>
  <div class="card">
      <div class="card-inner">

        <!-- gestione locandina film -->
        <div class="front" v-if="result.title">
          <img v-if="result.poster_path !== null" 
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Locandina ${result.title}`"
          >
          <h2 v-else>{{result.title}} <p>Nessuna locandina trovata</p> </h2>
        </div>

        <!-- gestione locandina serie tv -->
        <div class="front" v-else>
          <img v-if="result.poster_path !== null"
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Locandina ${result.name}`"
          >
          <h2 v-else>{{result.name}} <p>Nessuna locandina trovata</p> </h2>
        </div>

        <div class="back">
          <!-- all'interno della lista, ogni 'li' che varia da serie tv a film controlla di quale dei due si tratta tramite la direttiva v-if e si comporta di conseguenza scegliendo quale key dell'oggetto stampare a schermo -->
          <ul>
            <li>
              <strong>Titolo originale: </strong>
              <p v-if="result.original_title">
                {{result.original_title}}
              </p>
              <p v-else>{{result.original_name}}</p>
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
              <p v-if="result.title">
                {{result.title}}
              </p>
              <p v-else>{{result.name}}</p>
            </li>
            <li>
              <strong>Data di Uscita: </strong>
              <p v-if="result.release_date">
                {{result.release_date.split('-').reverse().join('/')}}
              </p>
              <p v-else>{{result.first_air_date.split('-').reverse().join('/')}}</p>
            </li>
            <li>
              <strong>Valutazione: </strong>
                <i v-for="index in getRating(result)" :key="`stars${index}`" 
                class="fas fa-star"></i>
                <i v-for="index in (MAX_STARS - getRating(result))" :key="`stars${index}`" 
                class="far fa-star"></i>

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
  },
  data(){
    return {
      MAX_STARS:5
    }
  },
  methods:{
    //divido per due arrotondando per eccesso il voto restituito dall'API e poi nel template stampo un numero di stelle corrispondente al voto
    getRating(result){
      return Math.ceil(result.vote_average / 2)
    }
  }
}
</script>

<style lang="scss">
@import '../assets/style/vars.scss';
@import '../assets/style/generals.scss';
  .card {
    width: calc(100% / 5 - 40px);
    margin: 20px;
    min-height: 400px;
    font-family: Arial, Helvetica, sans-serif;

    perspective: 1000px;
      .card-inner {
        position: relative;
        width: 100%;
        height: 100%;
        transition: all 0.8s;
        transform-style: preserve-3d;
        outline: 1px solid white;
        box-shadow: 0 10px 10px darken($bg-color, 15%);
        .front {
          font-family: "Bebas Neue";
          background-color: lighten($bg-color, 65%);
          img {
            width: 100%;  
            max-width: initial;
            height: 100%;
            max-height: initial;
          }
          h2 {
            padding: 0 10px;
            p {
             margin-top: 20px;
             font-size: 12px;
             font-family: Arial, Helvetica, sans-serif;
           }
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
      .front {
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
      }
      .back {
        padding-left: 7px;
        background-color: black;
        color: white;
        transform: rotateY(180deg);
      }
    ul {
      padding: 10px 0;
      li {
        padding-bottom: 20px;
        img.language-flag {
          width: 30px;
          vertical-align: middle;
        }
        i {
          color: gold;
        }
        p {
          display: inline-block;
        }
      }
    }
  }
</style>
