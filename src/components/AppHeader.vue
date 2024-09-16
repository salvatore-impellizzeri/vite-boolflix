<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
  data() {
    return {
      store,
    }
  },

  methods: {
    searchEvent(){
      if(this.store.SearchInput.length > 0)
      this.$emit('searchingEvent');
    }
  }

}
</script>

<template>
  <div class="container-fluid">
    <div class="bg-header row py-3 px-4 align-items-center">
      <h1 class="col-6 fw-medium">BOOLFLIX</h1>
      <div class="col-6 d-flex justify-content-end">
        <form @submit.prevent="searchEvent()">
          <input type="search" v-model="store.SearchInput" class="me-3" placeholder="Cerca un film...">
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