<template>
  <div class="card">
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
</template>

<script>
export default {
  name: 'CardSeries',
  props: {
    result: Object
  }
}
</script>

<style lang="scss" scoped>
  .card {
    width: calc(100% / 4 - 40px);
    margin: 20px;
    padding: 20px;
    background-color: tomato;
    min-height: 400px;
    font-family: Arial, Helvetica, sans-serif;
    // overflow: auto;
    ul {
      padding: 30px 0;
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