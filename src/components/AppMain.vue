<script>
import { store } from '../store.js';
import SingleCard from './SingleCard.vue';

export default {
  data() {
    return {
        store,
    }
  },
  methods: {
    handleScroll(event) {
      event.preventDefault();
      const container = event.currentTarget;
      const scrollAmount = container.clientWidth / 6; 
      
      if (event.deltaY > 0) {
        container.scrollLeft += scrollAmount;
      } else {
        container.scrollLeft -= scrollAmount;
      }
    },
  },

  components: {
    SingleCard,
  }
}
</script>

<template>
  <div class="section p-0">

    <!-- TRANDS -->

    <div v-if="this.store.MoviesList[0] == undefined">
      <div class="container-fluid bg-main">
        <h2 class="section-title">
          The best of the week
        </h2>
        <div class="row my-container-cards" @wheel="handleScroll">
          <div class="col-2 px-2 mb-4" v-for="(hits, index) in store.bestList" :key="index">
            <SingleCard 
              :title="hits.name"
              :originalTitle="hits.original_name"
              :language="hits.original_language"
              :vote="hits.vote_average"
              :overview="hits.overview"
              :image="hits.poster_path"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- MOVIE -->

    <div v-if="this.store.MoviesList[0] != undefined">
      <div class="container-fluid bg-main">
        <h2 class="section-title">
          Movies
        </h2>
        <div class="row my-container-cards" @wheel="handleScroll">
          <div class="col-2 px-2 mb-4" v-for="(movie, index) in store.MoviesList" :key="index">
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
    </div>

      <!-- SERIE TV -->

      <div v-if="this.store.MoviesList[0] != undefined">
        <div class="container-fluid bg-main">
          <h2 class="section-title">
            Series
          </h2>
          <div class="row my-container-cards" @wheel="handleScroll">
            <div class="col-2 px-2 mb-4" v-for="(serie, index) in store.SeriesList" :key="index">
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
    </div>
</template>

<style lang="scss" scoped>

h2{
  margin: 0;
}

.section {
  padding: 20px 0;  
}

.section-title {
  color: white;
  font-size: 25px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 1.5px;
  background-color: #1B1B1B;
}

.bg-main {
  padding: 20px;
  background-color: #1B1B1B;
}

.col-2 {
  scroll-snap-align: start;
  display: flex;
  justify-content: center;
}

.my-container-cards{
  padding: 20px 0;
  overflow-x: scroll;
  scroll-snap-type: x mandatory;
  scroll-behavior: smooth;
  flex-wrap: nowrap;
}

.my-container-cards::-webkit-scrollbar {
  display: none;
}

.my-container-cards:hover {
  cursor: grab;
}

</style>
