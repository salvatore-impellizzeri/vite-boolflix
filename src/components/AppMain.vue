<script>
import { store } from '../store.js';
import SingleCard from './SingleCard.vue';

export default {
  data() {
    return {
        store
    }
  },

  components: {
    SingleCard,
  }
}
</script>

<template> 
  <div class="container-fluid bg-main">
    <div class="p-4 row my-container-cards">
    <div class="col-2" v-for="(movie, index) in store.MovieList" :key="index">
      <SingleCard :movie="movie" />
    </div>
</div>
  </div>
</template>

<style lang="scss" scoped>
.bg-main{
    background-color: gray;
    min-height: 500px;
}

.my-container-cards{
    min-height: 300px;
}

</style>
