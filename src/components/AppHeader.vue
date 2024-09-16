<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
  data() {
    return {
      store,
      SearchMovie: '',
    }
  },

  methods: {
    reloadMovies() {
      if (this.SearchMovie.trim().length > 0) {
        axios
          .get(`https://api.themoviedb.org/3/search/movie?language=it-IT&api_key=4f7b343b6ae5c0e611d4ac0344a06a81&query=${this.SearchMovie}`)
          .then((res) => {
            store.searchMovie = res.data.results; 
            console.log('Risultati della ricerca:', res.data.results);
          })
          .catch((err) => {
            console.error('Errore durante la ricerca:', err);
            store.searchMovie = []; 
          });
      } else {
        console.log('La query di ricerca è vuota.');
      }
    }
  }
}
</script>

<template>
  <div class="container-fluid">
    <div class="bg-header row py-3 px-4 align-items-center">
      <h1 class="col-6 fw-medium">BOOLFLIX</h1>
      <div class="col-6 d-flex justify-content-end">
        <form @submit.prevent="reloadMovies">
          <input type="search" v-model="SearchMovie" class="me-3" placeholder="Cerca un film...">
          <button type="submit">Search</button>
        </form>
      </div>
    </div>
  </div>
</template>

<style>
.bg-header {
  background-color: black;
}

h1 {
  color: red !important;
}
</style>