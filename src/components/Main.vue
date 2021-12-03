<template>
  <main>
    <div class="film">
      <h2>Film</h2>
      <Card 
      v-for="item in moviesArray" 
      :key="item.id"
      :item="item" 
      />
    </div>

    <div class="serie">
      <h2>Serie tv</h2>
      <Card 
      v-for="item in seriesArray" 
      :key="item.id" 
      :item="item" 
      />  
    </div>
    
  </main>
</template>

<script>

import Card from './Card'

export default {
  name: 'Main',
  components: {
    Card
  },
  props:{
    moviesArray: Array,
    seriesArray: Array
  },

}
</script>

<style lang="scss">
  main{
    display: flex;
    flex-wrap: wrap;
    height: calc(100vh - 70px);
    background-color: rgb(23, 23, 23);
    color: white;
  }
</style>