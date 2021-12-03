<template>
  <main>
    <div>
      <h2>{{titleSection}}</h2>     
      <!-- <VueSlickCarousel v-bind="settings" v-if="listResult.length > 0"> -->
      <div class="title-section">
        <Card 
         v-for="item in listResult" 
        :key="item.id"
         :item="item" 
       />
      </div>
      <!-- </VueSlickCarousel> -->
    </div>
    
  </main>
</template>

<script>

import Card from './Card'
// import VueSlickCarousel from 'vue-slick-carousel'
// import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  name: 'Main',
  components: {
    Card,
    //VueSlickCarousel
  },
  props:{
    listResult: Array,
    titleSection: String
  },
  data() {
    return{
      settings:{
        "centerMode": true,
        "centerPadding": "20px",
        "focusOnSelect": true,
        "infinite": true,
        "slidesToShow": 3,
        "speed": 500
      }
    }
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