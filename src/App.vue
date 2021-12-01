<template>
  <div id="app">
    <Header 
      @sendSearch="getSearch"
    />
    <Main :resultList="apiResults"/>
  </div>
</template>

<script>

import Header from '../src/components/Header.vue'
import Main from '../src/components/Main.vue'

 import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data(){
    return {
      valueToSearch:'',
      apiResults: []
    }
  },
  methods:{

    callAPI(){
      //stringa statica con film di esempio. Ho scelto "Harry Potter" per provare
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=1f355eac8ba46b00364e7038d200138b&query=harry potter&language=it-IT')
        .then( r => {
          this.apiResults = r.data.results;
          console.log(this.apiResults);
        })
        .catch ( e => {
          console.log('ERRORE', e);
        })
    },

    getSearch(searchedValue){
      this.valueToSearch = searchedValue;
      this.callAPI();
    }
  }
}
</script>

<style lang="scss">
  @import "./assets/style/generals.scss";
  @import "./assets/style/vars.scss";
</style>
