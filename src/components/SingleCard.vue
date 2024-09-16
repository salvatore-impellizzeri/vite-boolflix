<script>
import { store } from '../store.js';

export default {
  data() {
    return {
        store,
        language: {
                EN: "https://flagsapi.com/GB/flat/64.png",
                JA: "https://flagsapi.com/JP/flat/64.png",
                IT: "https://flagsapi.com/IT/flat/64.png",
                FR: "https://flagsapi.com/FR/flat/64.png",
        }
    }
  },

   props: {
      movie: Object,
   },

  methods: {
    getFlagLanguage(){
        const languageCode = this.movie.original_language.toUpperCase();
        return this.language[languageCode] || "";
    }
  }
}
</script>

<template> 
    <div class="w-100 bg-dark border border-secondary my-container-card">
        <div>
            <!-- <img :src="`https://image.tmdb.org/t/p/original${movie.poster_path}`" alt="movie.title"> -->
        </div>
        <div class="text-white">
            <h3>{{ movie.title }}</h3>
            <h3>{{ movie.original_title }}</h3>
            <img :src="getFlagLanguage()" alt="" v-if="getFlagLanguage()">
            <h3>{{ movie.vote_average }}</h3>
        </div>
    </div>
</template>

<style scoped>
.my-container-card{
    min-height: 100px;
}
</style>
