<template>
  <div class="card">
      <div class="card-inner">
        <div class="front">
          <img v-if="result.poster_path !== null"
            class="poster" 
            :src="`https://image.tmdb.org/t/p/w342${result.poster_path}`" 
            :alt="`Locandina ${result.name}`"
          >
          <h2 v-else>{{result.name}}: <p>Nessuna locandina trovata</p> </h2>
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
</style>