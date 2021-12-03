<template>
<div>
  <div class="card">
    <div class="flip-card">
      <div class="flip-card-inner">
        <div class="flip-card-front">
          <img :src="`https://image.tmdb.org/t/p/w342/${item.poster_path}`" :alt="item.title || item.name">
        </div>
        <div class="flip-card-back">
          <h1>Titolo: {{item.title || item.name}}</h1>
          <p>Titolo originale: {{item.original_title || item.original_name}}</p>
          <p>
            Lingua: 
            <img class="flag" v-if="languageFlag() !== ''" :src="languageFlag()" :alt="item.original_language">
          </p>
          <p>
            Voto: 
            {{Math.round(item.vote_average/2)}}
            <i
              v-for="(star, index) in 5"
              :key="index"
              class="fa-star"
              :class="index < Math.round(item.vote_average/2) ? 'fas' : 'far' ">
            </i>
          </p>
        </div>
      </div>
    </div>
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
      const language = this.item.original_language;
      let img = '';

      if (language.toLowerCase().includes('it')) return img = require('../assets/img/it.png');
      if (language.toLowerCase().includes('en')) return img = require('../assets/img/it.png');

      return img;
    }
  }
}
</script>

<style lang="scss">
.flag{
  width: 20px;
}
.card{
  width: 100%;
  padding: 20px;
  display: flex;
  justify-content: space-between;
}
.flip-card {
  background-color: transparent;
  width: 250px;
  height: 350px;
  border: 1px solid #f1f1f1;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
  img{
    width: 100%;
    height: 100%;
  }
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
}

/* Style the back side */
.flip-card-back {
  background-color: dodgerblue;
  color: white;
  transform: rotateY(180deg);
}
</style>