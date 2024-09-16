<script>
import { store } from '../store.js';

export default {
  data() {
    return {
        store,
    }
  },

  methods: {
    urlImage(){
        return `https://image.tmdb.org/t/p/original${store.poster_path}`;
        console.log(this.urlImage);
    }
  }
}
</script>

<template> 
    <div class="w-100 bg-dark border border-secondary my-container-card">
        <div>
            <img :src="this.urlImage" alt="">
        </div>
    </div>
</template>

<style scoped>
.my-container-card{
    min-height: 100px;
}
</style>
