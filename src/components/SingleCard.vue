<script>
import { store } from '../store.js';

export default {
  data() {
    return {
        store,
        language: {
                ES: "https://flagsapi.com/ES/flat/64.png",
                EN: "https://flagsapi.com/GB/flat/64.png",
                JA: "https://flagsapi.com/JP/flat/64.png",
                IT: "https://flagsapi.com/IT/flat/64.png",
                DE: "https://flagsapi.com/DE/flat/64.png",
                FR: "https://flagsapi.com/FR/flat/64.png",
                RU: "https://flagsapi.com/RU/flat/64.png",
        },
        isHovered: false,
    }
  },

    props: {
      movie: Object,
    },

    methods: {
        getFlagLanguage(){
            const languageCode = this.movie.original_language.toUpperCase();
            return this.language[languageCode] || "";
        },

        handleMouseEnter() {
        this.isHovered = true;
        },

        handleMouseLeave() {
        this.isHovered = false;
        },
    }
}
</script>

<template> 
    <div class="w-100 bg-dark border border-secondary my-container-card my-3" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave">
        <div class="img-container">
            <div class="text-white desc" v-if="isHovered == true">
                <h3>
                    {{ movie.title }}
                </h3>
                <h3>
                    {{ movie.original_title }}
                </h3>
                <div>
                    <img :src="getFlagLanguage()" :alt="this.language[languageCode]" v-if="getFlagLanguage()">
                </div>
                <h3>
                    {{ movie.vote_average }}
                </h3>
            </div>
            <a href="#">
                <img :src="`https://image.tmdb.org/t/p/original${movie.poster_path}`" class="w-100" alt="movie.title">
            </a>
        </div>
    </div>
</template>

<style lang="scss" scoped>

.my-container-card{
    height: 600px;
    cursor: pointer;
    position: relative;

    .img-container{
        height: 600px;
        position: relative;

        img{
            height: 100%;
            object-fit: cover;
            transition: all 0.2s ease-in-out;
        }
       
        img:hover{
            opacity: 0.05;
            filter: blur(3px);
        }
    }

    .desc{
        position: absolute;
        top: 0px;
        left: 10px;
        opacity: 0;
        transition: all 0.2s ease-in-out;
    }

    .img-container:hover .desc {
        opacity: 1;
        top: 10px;
    }
}
</style>
