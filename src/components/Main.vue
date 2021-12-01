<template>
  <main>
    <div v-for="title in titleItems" :key="title.id" class="card">
      <p>Titolo: {{title.title}}</p>
      <p>Titolo originale: {{title.original_title}}</p>
      <p>Lingua: {{title.original_language}}</p>
      <p>Voto: {{title.vote_average}}</p>
    </div>
  </main>
</template>

<script>
export default {
  name: 'Main',
  data() {
    return {}
  },
  props:{
    titleItems: Array
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
    .card{
      width: 200px;
      padding: 20px;
    }
  }
</style>