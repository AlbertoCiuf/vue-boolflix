<template>
  <header>
    <div class="logo">
      <a href="#">
        <h1>boolflix</h1>
      </a>
    </div>
    <div class="search">
      <input type="text" placeholder="Cerca un film o una serie tv...">
      <div class="btn">Cerca</div>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
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
    }
    .search {
      display: flex;
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
        padding: 5px;
      }
    }
  }
</style>