<script>
import { store } from '../store.js';

export default {
  data() {
    return {

    }
  },

   props: {
      movie: Object,
   },

  methods: {

  }
}
</script>

<template> 
    <div class="w-100 bg-dark border border-secondary my-container-card">
        <div>
            <img :src="`https://image.tmdb.org/t/p/original${movie.poster_path}`" alt="movie.title">
        </div>
        <div>
            <h3>{{ movie.title }}</h3>
        </div>
    </div>
</template>

<style scoped>
.my-container-card{
    min-height: 100px;
}
</style>
