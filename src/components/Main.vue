<template>
  <main>
    
    <Card 
    v-for="film in titleItems.movie" 
    :key="film.id"
    :film="film" 
    />
 
    <!-- <Card 
    v-for="serie in titleItems.tv" 
    :key="serie.id" 
    :serie="serie" 
    />  -->
    
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
    titleItems: Object
  },
  computed: {
    
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