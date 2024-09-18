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

  }

}
</script>

<template>
  <div class="container-fluid">
    <div class="bg-header row py-4 px-4 align-items-center">
      <div class="col-6 fw-medium">
        <img src="https://image.tmdb.org/t/p/w200/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
      </div>
      <div class="col-6 d-flex justify-content-end">
        <form @submit.prevent="search">
          <input type="search" v-model="store.SearchInput" class="me-3" placeholder="Cerca un film...">
          <button @click="search" type="submit">Cerca</button>
        </form>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.bg-header {
  background-color: black;
}

input{
  background-color: transparent;
  border-radius: 20px;
  padding: 5px 10px;
  color: white;
}

button{
  border-radius: 20px !important;
  border: 1px solid rgb(255, 255, 255);
  background-color: transparent;
  color: white;
  padding: 5px 15px;
}

h1 {
  color: red !important;
}
</style>