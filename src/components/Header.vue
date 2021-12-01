<template>
  <header>
    <div class="logo">
      BoolFlix
    </div>
    <div class="search-bar">
      <input
       type="text" 
       placeholder="Inserisci un titolo"
       v-model="searchText"
      />
      <button @click="search">Cerca</button>
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
      console.log(this.searchText);
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
    background: dimgray;
    .logo{
      background-color: white;
      border-radius: 50%;
      padding: 20px 10px;
    }
    .search-bar{
      input{
        padding: 10px 30px;
      }
      button{
        padding: 10px 20px;
      }
    }
  }
</style>