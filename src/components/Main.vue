<template>
  <main>
    <div class="card"
      v-for="(item, index) in resultList" :key="`cardN${index}`"
    >
      <ul>
        <li>
          <strong>Titolo originale: </strong>
          <p>{{item.original_title}}</p>
          </li>
        <li>
        <li>
          <strong>Lingua originale: </strong>
          <p>{{item.original_language}}</p>
          </li>
        <li>
          <strong>Titolo: </strong>
          <p>{{item.title}}</p>
        </li>
        <li>
          <strong>Data di Uscita: </strong>
          <p>{{item.release_date.split('-').reverse().join('/')}}</p>
        </li>
        <li>
          <strong>Valutazione: </strong>
          <p>{{item.vote_average}}</p>
        </li>
        <li>
          <strong>Descrizione: </strong>
          <p v-if=" item.overview !== '' ">
            {{item.overview}}
          </p>
          <p v-else>N/A</p>
        </li>
        
      </ul>
    </div>
  </main>
</template>

<script>
export default {
  name: 'Main',
  data(){
    return {
    }
  },
  props: {
    resultList: Array
  },
  methods: {
    
  },
  mounted(){
    console.log(this.resultList);
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
    .card {
      width: calc(100% / 4 - 40px);
      margin: 20px;
      padding: 20px;
      background-color: tomato;
      min-height: 400px;
      font-family: Arial, Helvetica, sans-serif;
      ul {
        padding: 50px 0;
        li {
          padding-bottom: 15px;
          p {
            display: inline-block;
          }
        }
      }
    }
  }
</style>