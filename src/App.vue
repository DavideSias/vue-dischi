<template>
  <div>
    <header-page @change="onFiltersChange"/>
    <main-page :selectedValue="selectedValue"/>
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
      selectedValue: 'none',
    };
  },
  methods: {
    onFiltersChange(newSelectedValue) {
      this.selectedValue = newSelectedValue;
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
