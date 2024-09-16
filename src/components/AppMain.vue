<script>
import { store } from '../store.js';
import SingleCard from './SingleCard.vue';

export default {
  data() {
    return {
        store,
        SingleCard,
    }
  }
}
</script>

<template> 
  <div class="container-fluid bg-main">
    <div class="p-4 row my-container-cards">
        <SingleCard v-for="(movie, i) in SearchMovie" class="col-2" />
    </div>    
  </div>
</template>

<style scoped>
.bg-main{
    background-color: gray;
    min-height: 500px;
}

</style>
