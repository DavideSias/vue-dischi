<template>
  <div>
    <header-page />
    <main-page />
  </div>
</template>

<script>
import HeaderPage from './components/HeaderPage.vue';
import MainPage from './components/MainPage.vue';

export default {
  components: {
    HeaderPage,
    MainPage,
  },

};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
body {
  background-color: rgb(30, 45, 59);
}
</style>
