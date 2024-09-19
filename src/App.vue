<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from './store.js';

export default {
  data() {
    return {
      moviesUrl: 'https://api.themoviedb.org/3/search/movie?api_key=',
      seriesUrl: 'https://api.themoviedb.org/3/search/tv?api_key=',
      store,
      apiKey: '4f7b343b6ae5c0e611d4ac0344a06a81',
      token: 'eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiI0ZjdiMzQzYjZhZTVjMGU2MTFkNGFjMDM0NGEwNmE4MSIsIm5iZiI6MTcyNjQ4NDkwNS4xNTY1NTQsInN1YiI6IjY2ZTdmYTVjMDUwZjE0ZTRmY2NmZTk5MyIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.Nn8FnahEX-u0kxqw8GDJ56eLeuIwwMzVY7Z99QUvXLU',
    }
  },

  components: {
    AppHeader,
    AppMain,
  },

  created() {
    axios
    axios.get('https://api.themoviedb.org/3/trending/tv/week?language=it-IT', {
        headers: {
            'Authorization': `Bearer ${this.token}`
        }
    })
    .then((res) => {
        this.store.bestList = res.data.results;
    })
    .catch((error) => {
        console.log(error);
    })
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
    <AppHeader class="header" @search="search"/>
  </div>
  <div>
    <AppMain />
  </div>
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";


.header{
  position: relative;
}

</style>

