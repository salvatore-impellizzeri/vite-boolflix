<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import { store } from './store.js';
import axios from 'axios';

export default {
  data() {
    return {
      movieUrl: 'https://api.themoviedb.org/3/search/movie?api_key=4f7b343b6ae5c0e611d4ac0344a06a81',
      seriesUrl: 'https://api.themoviedb.org/3/search/tv?api_key=4f7b343b6ae5c0e611d4ac0344a06a81',
      store,
    }
  },

  components: {
    AppHeader,
    AppMain,
    AppFooter,
  },

  methods: {
    callApi(){
      axios
        .get(this.movieUrl + "&query=" + store.SearchInput)
        .then((res) => {
          this.store.MovieList = res.data.results;
        })
        .catch((err) => {
          console.error('Errore durante la chiamata API:', err);
        });

      axios
        .get(this.seriesUrl + "&query=" + store.SearchInput)
        .then((response) => {
          this.store.SeriesList = response.data.results;
        })
        .catch((err) => {
          console.error('Errore durante la chiamata API:', err);
        });  
    }
  },
}
</script>

<template> 
  <div>
    <AppHeader @searchingEvent="callApi"/>
  </div>
  <div>
    <AppMain />
  </div>
  <div>
    <AppFooter />
  </div>
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";


</style>

