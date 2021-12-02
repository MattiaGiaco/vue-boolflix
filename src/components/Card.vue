<template>
<div>
  <div class="card">
    <p>Titolo: {{film.title}}</p>
    <p>Titolo originale: {{film.original_title}}</p>
    <p>Lingua: {{film.original_language}}</p>
    <p>Voto: {{film.vote_average}}</p>
  </div>
 
  <!-- <div class="card">
    <p>Titolo: {{serie.name}}</p>
    <p>Titolo originale: {{serie.original_name}}</p>
    <p>Lingua: {{serie.original_language}}</p>
    <p>Voto: {{serie.vote_average}}</p>
  </div> -->
</div>
</template>

<script>

export default {
  name: 'Card',
  props:{
    film: Object,
    serie: Object
  },
  data() {
    return {}
  },
}
</script>

<style lang="scss">
.card{
  width: 200px;
  padding: 20px;
}
</style>