<template>
  <div>
    <header-page :genres-list="genresList" @changedGenre="genreChange"/>
    <main-page @genresReady="getGenresList" :genre-filter="genreFilter"/>
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
  data() {
    return {
      genresList: [],
      genreFilter: 'all',
    };
  },
  methods: {
    getGenresList(genresList) {
      this.genresList = genresList;
    },
    genreChange(genreFilter) {
      this.genreFilter = genreFilter;
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
body {
  background-color: rgb(30, 45, 59);
}
</style>
