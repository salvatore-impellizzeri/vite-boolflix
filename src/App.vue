<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js';
import axios from 'axios';

export default {
  data() {
    return {
      moviesUrl: 'https://api.themoviedb.org/3/search/movie?api_key=',
      seriesUrl: 'https://api.themoviedb.org/3/search/tv?api_key=',
      store,
      apiKey: '4f7b343b6ae5c0e611d4ac0344a06a81',
    }
  },

  components: {
    AppHeader,
    AppMain,
  },

  created() {
    // axios
    //   .get(`https://api.themoviedb.org/3/trending/all/day?4f7b343b6ae5c0e611d4ac0344a06a81&language=it-IT`)
    //   .then((res) => {
    //       this.store.moviesList = res.data.results;
    //       console.log(res.data.results, typeof res.data);
    //   })
    //   .catch((error) => {
    //       console.error(error)
    //   })
  },  

  methods: {
    search() {
      axios
        .get(this.moviesUrl + this.apiKey + "&query=" + store.SearchInput)
        .then((res) => {
          this.store.MoviesList = res.data.results;
        })
        .catch((err) => {
          console.error('Errore durante la chiamata API:', err);
        });

      axios
        .get(this.seriesUrl + this.apiKey + "&query=" + store.SearchInput)
        .then((response) => {
          this.store.SeriesList = response.data.results;
          console.log(this.store.SeriesList)
        })
        .catch((err) => {
          console.error('Errore durante la chiamata API:', err);
        });
    },
  }
}

</script>

<template> 
  <div>
    <AppHeader @search="search"/>
  </div>
  <div class="bg">
    <AppMain />
  </div>
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";

.bg{
  background-color: #121212;
}

</style>

