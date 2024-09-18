<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
  data() {
    return {
      store,
    }
  },
}
</script>

<template>
  <div class="container-fluid">
    <div class="bg-header row py-4 px-4 align-items-center">
      <div class="col-4 fw-medium">
        <img src="https://image.tmdb.org/t/p/w200/wwemzKWzjKYJFfCeiB57q3r4Bcm.png" alt="">
      </div>
      <div class="col-4 d-flex justify-content-end">
        <form @submit.prevent="search" class="w-100">
          <input type="search" v-model="store.SearchInput" class="me-3 w-75" placeholder="Cerca un film...">
          <button @click="search" type="submit">Cerca</button>
        </form>
      </div>
      <div class="col-4 d-flex justify-content-end">
        <ul class="nav justify-content-end">
          <li class="nav-item">
            <a class="nav-link fw-bold active" aria-current="page" href="#">Home</a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-mediumm" href="#">Serie TV</a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-mediumm" href="#">Film</a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-mediumm" href="#">Originali</a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-mediumm" href="#">Aggiunti di recente</a>
          </li>
          <li class="nav-item">
            <a class="nav-link fw-mediumm" href="#">La mia lista</a>
          </li>
        </ul>
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

.nav-link{
  color: white !important;
}
</style>