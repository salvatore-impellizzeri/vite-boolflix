<script>
import { store } from '../store.js';
import SingleCard from './SingleCard.vue';

export default {
  data() {
    return {
        store,
    }
  },

  components: {
    SingleCard,
  }
}
</script>

<template>
  <div class="section p-0">
    <h2 class="section-title p-4">
      Movies
    </h2>
    <div class="container-fluid bg-main">
      <div class="row my-container-cards">
        <div class="col-2 mb-4" v-for="(movie, index) in store.MoviesList" :key="index">
          <SingleCard 
            :title="movie.title"
            :originalTitle="movie.original_title"
            :language="movie.original_language"
            :vote="movie.vote_average"
            :overview="movie.overview"
            :image="movie.poster_path"
          />
        </div>
      </div>
    </div>

    <h2 class="section-title p-4">
      Series
    </h2>
    <div class="container-fluid bg-main">
      <div class="row my-container-cards">
        <div class="col-2 mb-4" v-for="(serie, index) in store.SeriesList" :key="index">
          <SingleCard 
            :title="serie.name"
            :originalTitle="serie.original_name"
            :language="serie.original_language"
            :vote="serie.vote_average"
            :overview="serie.overview"
            :image="serie.poster_path"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>

.section {
  padding: 20px 0;  
}

.section-title {
  box-shadow: 0px 0px 10px white;
  color: white;
  font-size: 32px;
  font-weight: bold;
  text-align: center;
  text-transform: uppercase;
  letter-spacing: 1.5px;
}

.bg-main {
  background-color: rgb(34, 34, 34);
  padding: 20px;
  border-radius: 10px;
}

.col-2 {
  display: flex;
  justify-content: center;
}

</style>
