<template>
  <div id="app">
    <Header @newSearch="searchTitle" />
    <Main :titleItems="foundTitles" />
    
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    Main,
    Header
  },
  data() {
    return {
      apiKey: '3118cc2a73813a973ac86114f6cf4895',
      baseURL: 'https://api.themoviedb.org/3/search/movie?api_key=',
      foundTitles: [],
      isLoading: false
    }
  },
  methods:{
    searchTitle(title) {
      console.log('titolo inserito', title);

      this.isLoading = true;
      axios.get(`${this.baseURL+this.apiKey}&query=${title}&language=it-IT`)
        .then(r => {
          console.log(r);
          this.foundTitles = r.data.results;
          this.isLoading = false

        }).catch(error => {
          console.log(error);
        })
    }
  }
}
</script>

<style lang="scss">

@import './assets/style/generals.scss';

</style>
