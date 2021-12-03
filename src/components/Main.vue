<template>
  <main>
    <div class="title-section">
      <h2>{{titleSection}}</h2>
      <Card 
      v-for="item in listResult" 
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
    listResult: Array,
    titleSection: String
  },

}
</script>

<style lang="scss">
  main{
    display: flex;
    height: 50%;
    color: white;
    .title-section{
      display: flex;
      
      width: 100%;
    }
  }
</style>