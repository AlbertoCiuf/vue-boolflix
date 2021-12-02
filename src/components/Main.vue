<template>
  <main>

      <Card 
        v-for="item in resultList" 
        :key="item.id" 
        :result="item"
      />

  </main>
</template>

<script>
import Card from './Card.vue'
export default {
  name: 'Main',
  components: {
    Card
  },
  
  props: {
    resultList: Array
  },
 
}
</script>

<style lang="scss" scoped>
  @import '../assets/style/vars.scss';
  main {
    min-height: calc(100vh - 120px);
    background-color: $bg-color;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    padding: 50px 100px;
  }
</style>