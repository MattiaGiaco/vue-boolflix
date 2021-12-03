<template>
  <header>
    <div class="logo">
      <h1>BoolFlix</h1>
    </div>
    <div class="search-bar">
      <input
       type="text" 
       placeholder="Inserisci un titolo"
       v-model="searchText"
       @keyup.enter="search"
      />
      <button @click="search"><h4>Cerca</h4></button>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      searchText: ''
    }
  },
  methods:{
    search() {
      this.$emit('newSearch', this.searchText);
      //console.log(this.searchText);
    }
  }
}
</script>

<style lang="scss">

  header{
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 70px;
    padding: 0 30px;
    background: linear-gradient(black, rgba(23,23,23));
    .logo{
      color: rgb(226, 21, 21);
    }
    .search-bar{
      input{
        padding: 10px 30px;
        border-radius: 10px;
        border: none;
      }
      button{
        padding: 10px 20px;
        border-radius: 10px;
        border: none;
        margin-left: 10px;
        background-color: whitesmoke;
        cursor: pointer;
        &:hover h4{
          color: rgb(226, 21, 21);
        }
      }
    }
  }
</style>