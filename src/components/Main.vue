<template>
  <main>
    
    <Card 
    v-for="item in moviesArray" 
    :key="item.id"
    :item="item" 
    />
 
    <Card 
    v-for="item in seriesArray" 
    :key="item.id" 
    :item="item" 
    />  
    
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
  computed: {
    
  },
  methods: {
    
  }

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