<template>
  <div id="app">
    <Header @newSearch="searchTitle" />
    <Main />
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Main from './components/Main.vue'
//import axios from 'axios'


export default {
  name: 'App',
  components: {
    Main,
    Header
  },
  data() {
    return {
      apiKey: '3118cc2a73813a973ac86114f6cf4895',
      baseURL: 'https://api.themoviedb.org/3/movie/76341?api_key='
    }
  },
  methods:{
    searchTitle(title) {
      console.log('titolo inserito', title);
    }
  }
}
</script>

<style lang="scss">

@import './assets/style/generals.scss';

</style>
