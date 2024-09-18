<script>
import { store } from '../store.js';

export default {
  data() {
    return {
        store,
        isHovered: false,
    }
  },

    props: {
      title: String,
      originalTitle: String,
      language: String,
      vote: Number,
      overview: String,
      image: String,
    },

    methods: {
        
        averageVote(){
            return Math.round(this.vote/2);
        },  

        getFlagLanguage(){
            const languageCodes = {
                ES: "https://flagsapi.com/ES/flat/64.png",
                EN: "https://flagsapi.com/GB/flat/64.png",
                JA: "https://flagsapi.com/JP/flat/64.png",
                IT: "https://flagsapi.com/IT/flat/64.png",
                DE: "https://flagsapi.com/DE/flat/64.png",
                FR: "https://flagsapi.com/FR/flat/64.png",
                RU: "https://flagsapi.com/RU/flat/64.png",
            };
            const languageCode = this.language.toUpperCase();
            return languageCodes[languageCode] || "";
        },

        handleMouseEnter() {
        this.isHovered = true;
        console.log("Mouse entered")
        },

        handleMouseLeave() {
        this.isHovered = false;
        console.log("Mouse Left")
        },
    }
}
</script>

<template> 
    <div class="w-100 bg-dark border border-secondary my-container-card my-3" @mouseenter="handleMouseEnter()" @mouseleave="handleMouseLeave()">
        <div class="img-container">
            <div class="text-white m-3 desc" v-if="isHovered == true">
                <h4>
                    Titolo: <span>{{ title }}</span>
                </h4>
                <h4>
                    Titolo originale: <span>{{ originalTitle }}</span>
                </h4>
                <h4>
                    Voto: 
                    <span v-for="index in 5" :key="index">
                        <i class="fa-star" :class="averageVote() >= index ? 'fa-solid' : 'fa-regular'"></i>
                    </span> 
                </h4>
                <div class="d-flex align-items-center gap-3">
                    <h4>
                        Lingua originale:
                    </h4>
                    <img class="img-flag" :src="getFlagLanguage()" :alt="this.language" v-if="getFlagLanguage()">
                </div>
                <h4>
                    Overview: <span v-if="overview.length > 0" class="last-message">{{ overview.length > 355 ? overview.slice(0, 355) + "..." : overview }}</span>
                </h4>
            </div>
            <a href="#">
                <img :src="`https://image.tmdb.org/t/p/original${image}`" class="w-100 img-bg" :alt="title">
            </a>
        </div>
    </div>
</template>

<style scoped>

.fa-solid{
    color: rgb(214, 214, 0);
}

.my-container-card{
    cursor: pointer;
}

.img-flag{
    width: 40px;
}

.img-container{
    position: relative;
    height: 600px; 
}

.img-bg{
    height: 100%;
    object-fit: cover;
    transition: all 0.2s ease-in-out;
}

.img-container:hover .img-bg{
    opacity: 0.05;
    filter: blur(3px);
}

.desc{
    height: 500px;
    position: absolute;
    top: 0px;
    left: 0;
    opacity: 0;
    transition: all 0.2s ease-in-out;
}

.img-container:hover .desc {
    opacity: 1;
}

</style>
