<template>
  <main>
    <h2 v-if="resultListMovies.length > 0">Film</h2>
    <section class="film">
      <Card 
        v-for="item in resultListMovies" 
        :key="item.id" 
        :result="item"
      />
    </section>
    <h2 v-if="resultListSeries.length > 0">Serie TV</h2>
    <section class="film">
      <CardSeries 
        v-for="item in resultListSeries" 
        :key="item.id" 
        :result="item"
      />
    </section>

  </main>
</template>

<script>
import Card from './Card.vue'
import CardSeries from './CardSeries.vue'
export default {
  name: 'Main',
  components: {
    Card,
    CardSeries
  },
  props: {
    resultListMovies: Array,
    resultListSeries: Array,
  },
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
    }
    section.film {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
    }
  }
</style>