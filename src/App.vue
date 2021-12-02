<template>
  <div id="app">
    <Header 
      @sendSearch="getSearch"
    />
    <Main 
      :resultList="apiResults"
    />
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
      apiResults: [],
      // apiUrl: 'https://api.themoviedb.org/3/search/',
      // searchTypeMovie: 'movie',
      // apiKey: '1f355eac8ba46b00364e7038d200138b',
    }
  },
  methods:{
    callAPI(){
      
      //concateno in template literal i vari data per comporre l'url che chiama l'API
      //axios.get(`${this.apiUrl}${this.searchTypeMovie}?api_key=${this.apiKey}&query=${this.valueToSearch}&language=it-IT`)

      //chiamo l'api e gestisco la ricerca dinamicamente con params:{} - come query è impostato this.valueToSearch, che è il v-model che rende dinamica e funzionante la ricerca
      axios.get('https://api.themoviedb.org/3/search/movie',{
        params: {
          api_key: '1f355eac8ba46b00364e7038d200138b',
          query: this.valueToSearch,
          language: 'it-IT'
        }
      })
        .then( r => {
          this.apiResults = r.data.results;
          console.log(this.apiResults);
        })
        .catch( e => {
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
