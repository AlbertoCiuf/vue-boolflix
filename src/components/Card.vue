<template>
  <div class="card">
      <ul>
        <li>
          <strong>Titolo originale: </strong>
          <p>{{result.original_title}}</p>
        </li>
        <li>
          <strong>Lingua originale: </strong>
          <p>{{result.original_language}}</p>
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
</template>

<script>
export default {
  name: 'Card',
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
    ul {
      padding: 30px 0;
      li {
        padding-bottom: 20px;
        p {
          display: inline-block;
        }
      }
    }
  }
</style>