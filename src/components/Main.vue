<template>
  <main>
    <div class="wrapper">
      <!-- messaggio di default al caricamento della pagina o al reset della ricerca -->
      <div class="default-msg"
        v-if="resultListMovies.length <= 0 && resultListSeries.length <= 0"
      >
        <h2>Inizia a cercare qualcosa...</h2>
      </div>

      <div v-else class="content">

        <!-- elenco film -->
        <h2 v-if="resultListMovies.length > 0">Film</h2>
        <section class="film">
          <Card 
            v-for="item in resultListMovies" 
            :key="item.id" 
            :result="item"
          />
        </section>

        <!-- elenco serie tv -->
        <h2 v-if="resultListSeries.length > 0">Serie TV</h2>
        <section class="serie">
          <Card 
            v-for="item in resultListSeries" 
            :key="item.id" 
            :result="item"
          />
        </section>
      </div>

    </div>

  </main>
</template>

<script>
import Card from './Card.vue'
export default {
  name: 'Main',
  components: {
    Card,
  },
  props: {
    resultListMovies: Array,
    resultListSeries: Array,
  }
}
</script>

<style lang="scss" scoped>
  @import '../assets/style/vars.scss';
  main {
    min-height: calc(100vh - 120px);
    background-color: $bg-color;
    padding: 50px 100px;
    h2 {
      color: #fff;
      font-size: 40px;
      text-shadow: 5px 10px 10px darken($bg-color, 15%);
    }
    section.film, section.serie {
      display: flex;
      flex-wrap: wrap;
    }
  }

</style>