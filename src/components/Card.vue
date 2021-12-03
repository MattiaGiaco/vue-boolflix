<template>
<div>
  <div class="card">
    <p>Titolo: {{item.title}}</p>
    <p>Titolo originale: {{item.original_title}}</p>
    <p>Lingua: {{item.original_language}}</p>
    <p>Voto: {{item.vote_average}}</p>
  </div>
 
 <div class="card">
    <p>Titolo: {{item.name}}</p>
    <p>Titolo originale: {{item.original_name}}</p>
    <p>Lingua: {{item.original_language}}</p>
    <p>Voto: {{item.vote_average}}</p>
  </div> 
</div>
</template>

<script>

export default {
  name: 'Card',
  props:{
    item: Object
  },
  data() {
    return {}
  },
  methods: {
    languageFlag(){
      const language = this.film.original_language;
      let img = '';

      if (language.toLowerCase().includes('it')) return img = require('../assets/img/it.png');
      if (language.toLowerCase().includes('en')) return img = require('../assets/img/it.png');

      return img;
    }
  }
}
</script>

<style lang="scss">
.card{
  width: 200px;
  padding: 20px;
}
</style>