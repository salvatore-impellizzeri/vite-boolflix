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
  <h2>
    Movies
  </h2>
  <div class="container-fluid bg-main">
    <div class="p-4 row my-container-cards">
      <div class="col-2" v-for="(movie, index) in store.MoviesList" :key="index">
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

  <h2>
    Series
  </h2>
  <div class="container-fluid bg-main">
    <div class="p-4 row my-container-cards">
      <div class="col-2" v-for="(serie, index) in store.SeriesList" :key="index">
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
</template>

<style lang="scss" scoped>

.bg-main{
    background-color: rgb(34, 34, 34);
}

.my-container-cards{
    min-height: 300px;
}

</style>
