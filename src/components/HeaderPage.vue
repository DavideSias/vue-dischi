<template>
  <div class="navbar p-2">
    <img src="@/img/logo-small.svg" alt="logo">
    <select-genre @change="onChange"/>
  </div>
</template>

<script>
import SelectGenre from './SelectGenre.vue';

export default {
  name: 'HeaderPage',
  components: { SelectGenre },
  data: () => ({
    value: 'none',
  }),
  methods: {
    onChange(selectedValue) {
      this.$emit('change', selectedValue);
    },
  },
};
</script>

<style lang="scss" scoped>
.navbar{
  background-color: rgb(46, 58, 70);
  img{
    width: 35px;
  }
}
</style>
