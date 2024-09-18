<script>
import axios from 'axios';
import { store } from '../store.js';

export default {
  data() {
    return {
      store,
      links: [
        {
          label:"Home",
          href:"#",
        },
        {
          label:"Serie TV",
          href:"#",
        },
        {
          label:"Film",
          href:"#",
        },
        {
          label:"Originali",
          href:"#",
        },
        {
          label:"Aggiunti di recente",
          href:"#",
        },
        {
          label:"La mia lista",
          href:"#",
        },
      ],
      active: 0,
    }
  },

  methods: {
    toggleLink(index){
      this.active = index;
    }
  }
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
          <button @click="search" class="btn btn-light fw-medium" type="submit">Cerca</button>
        </form>
      </div>
      <div class="col-4 d-flex justify-content-end">
        <ul class="nav gap-4 justify-content-end">
          <li class="nav-item" v-for="(link, index) in links" key="index">
            <a :href="link.href" @click="toggleLink(index)" :class="{ 'active-text' : active === index }">
              {{ link.label }}
            </a>
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
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.466);
  padding: 5px 10px;
  color: white;
}

button{
  border-radius: 20px !important;
}

h1 {
  color: red !important;
}

.nav-link{
  color: rgba(255, 255, 255, 0.637) !important;
}

.active-text{
  font-weight: bold;
  color: white;
}

li > a{
  text-decoration: none;
  color: rgba(223, 223, 223, 0.7);
  height: 100%;
  display: flex;
  align-items: center;
}

</style>