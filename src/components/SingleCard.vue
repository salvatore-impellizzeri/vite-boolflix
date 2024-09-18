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
    averageVote() {
        return Math.round(this.vote / 2);
    },  

    getFlagLanguage() {
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
        console.log("Mouse entered");
    },

    handleMouseLeave() {
        this.isHovered = false;
        console.log("Mouse Left");
    },
  }
}
</script>

<template> 
  <div class="card-container" @mouseenter="handleMouseEnter" @mouseleave="handleMouseLeave">
    <div class="img-container">
      <div class="desc" v-if="isHovered">
        <div class="info-container p-3">
          <h3 class="title">{{ title }}</h3>
          <h4 class="original-title">Titolo originale: {{ originalTitle }}</h4>
          <div class="rating">
            <span v-for="index in 5" :key="index">
              <i class="fa-star" :class="averageVote() >= index ? 'fa-solid' : 'fa-regular'"></i>
            </span>
          </div>
          <div class="d-flex align-items-center justify-content-center gap-2 mt-2">
            <span>Lingua originale:</span>
            <img class="img-flag" :src="getFlagLanguage()" :alt="language" v-if="getFlagLanguage()">
          </div>
          <p class="overview mt-3">{{ overview.length > 355 ? overview.slice(0, 355) + "..." : overview }}</p>
        </div>
      </div>
      <img :src="`https://image.tmdb.org/t/p/original${image}`" class="img-bg" :alt="title">
    </div>
  </div>
</template>

<style scoped>

.card-container {
    cursor: pointer;
    position: relative;
    overflow: hidden;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.card-container:hover {
    transform: scale(1.05);
    box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
}

.img-container {
    position: relative;
    height: 600px;
    overflow: hidden;
    border-radius: 10px;
}

.img-bg {
    height: 100%;
    width: 100%;
    object-fit: cover;
    transition: all 0.3s ease;
}

.card-container:hover .img-bg {
    opacity: 0.1;
    filter: blur(5px);
}

.desc {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgba(0, 0, 0, 0.75);
    opacity: 1;
    transition: all 0.3s ease;
}

.info-container {
    text-align: center;
    color: #fff;
}

.title {
    font-size: 24px;
    font-weight: bold;
}

.original-title {
    font-size: 16px;
}

.rating {
    margin-top: 8px;    
}

.fa-star {
    font-size: 19px; 
}

.fa-solid {
    color: rgb(214, 214, 0);
}

.fa-regular {
    color: rgb(120, 120, 120);
}

.img-flag {
    width: 32px;
    height: auto;
}

.overview {
    font-size: 14px;
    line-height: 1.4;
    color: rgba(255, 255, 255, 0.8);
    max-height: 150px;
}
</style>
