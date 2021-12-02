<template>
  <div id="app">
    <Header @newSearch="searchTitle" />
    <div v-if="isLoading" class="loading">
      <Loading title="Caricamento titoli..."/>
    </div>
    <div v-else >
      <Main :titleItems="foundTitles" />
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
      media: {
        movie: 'movie',
        tv: 'tv'
      },
      foundTitles: {
        movie: [],
        tv: []
      },
      isLoading: false
    }
  },
  methods:{
    searchTitle(title) {
      console.log('titolo inserito', title);
      this.apiParams.query = title;
      this.getApi(this.media.movie);
      this.getApi(this.media.tv);
    },
    getApi(media){
      this.isLoading = true;
      axios.get(this.baseURL + media,{params:this.apiParams})
        .then(r => {
          //console.log(r);
          console.log('media',media);
          this.foundTitles[media] = r.data.results;
          //console.log(this.foundTitles);
          console.log('movies:',this.foundTitles.movie);
          console.log('series:',this.foundTitles.tv);
          
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
