<template>
  <div id="app">
    <Header @newSearch="searchTitle" />
    <div v-if="isLoading" class="loading">
      <Loading title="Caricamento titoli..."/>
    </div>
    <div v-else >
      <Main 
        :moviesArray="moviesArray" 
        :seriesArray="seriesArray" 
      />
    </div>
    
  </div>
</template>

<script>

import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Loading from './components/Loading.vue'
import axios from 'axios'


export default {
  name: 'App',
  components: {
    Main,
    Header,
    Loading
  },
  data() {
    return {
      baseURL: 'https://api.themoviedb.org/3/search/',
      apiParams:{
        api_key: '3118cc2a73813a973ac86114f6cf4895',
        query: '',
        language: 'it-IT',
      },
      moviesArray: [],
      seriesArray: [],
      isLoading: false
    }
  },
  methods:{
    searchTitle(title) {
      console.log('titolo inserito', title);
      this.apiParams.query = title;
      this.getApi()
    },
    getApi(){
      this.isLoading = true;
      axios.get(this.baseURL + 'movie' ,{params:this.apiParams})
        .then(r => {
          //console.log(r);
          
          this.moviesArray = r.data.results;

          console.log('moviesArray',this.moviesArray);
          
          this.isLoading = false

        }).catch(error => {
          console.log(error);
        })

      axios.get(this.baseURL + 'tv' ,{params:this.apiParams})
        .then(r => {
          //console.log(r);
          
          this.seriesArray = r.data.results;

          console.log('seriesArray',this.seriesArray);
          
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

.loading{
  height: calc(100vh - 70px);
  background-color: rgb(23, 23, 23);
}

</style>
