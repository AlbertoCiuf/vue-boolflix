<template>
  <header>
    <div class="logo">
      <a href="#">
        <h1>boolflix</h1>
      </a>
    </div>
    <div class="search">
      <input type="text" placeholder="Cerca un film o una serie tv..."
        v-model="searchedValue"
        @keyup.enter="callSearch"
      >
      <div class="btn"
        @click="callSearch"
      >
        Cerca
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data(){
    return {
      searchedValue:''
    }
  },
  methods: {
    callSearch(){
      this.$emit('sendSearch', this.searchedValue);
    }
  }
}
</script>

<style lang="scss" scoped>
  header {
    height: 120px;
    padding: 0 20px;
    background-color: black;
    display: flex;
    align-items: center;
    justify-content: space-between;
    a h1 {
      color: red;
      font-size: 48px;
      transition: all .3s;
      &:hover {
        transform: scale(1.1);
      }
    }
    .search {
      display: flex;
      align-items: center;
      input {
        height: 30px;
        width: 500px;
        margin-right: 10px;
        padding: 5px;
      }
      .btn {
        background-color: red;
        color: white;
        font-family: Arial, Helvetica, sans-serif;
        padding: 5px 10px;
        cursor: pointer;
        transition: all .3s;
        &:hover {
        transform: scale(1.1);
        }
      }
    }
  }
</style>