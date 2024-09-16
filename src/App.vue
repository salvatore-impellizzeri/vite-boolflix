<script>
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import { store } from './store.js';

export default {
  data() {
    return {
      message: 'Template Vite + Vue'
    }
  },

  components: {
    AppHeader,
    AppMain,
    AppFooter,
  }
}
</script>

<template> 
  <div>
    <AppHeader />
  </div>
  <div>
    <AppMain />
  </div>
  <div>
    <AppFooter />
  </div>
</template>

<style lang="scss">
@import "bootstrap/scss/bootstrap";


</style>

