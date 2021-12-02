<template>
  <div class="card">
      <div class="card-inner">
        <div class="front">
          <img v-if="result.poster_path !== null" 
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Locandina ${result.title}`"
          >
          <h2 v-else>{{result.title}}: <p>Nessuna locandina trovata</p> </h2>
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
