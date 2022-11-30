<template>
  <div class="navbar p-2">
    <img src="@/img/logo-small.svg" alt="logo">
    <label for="select-genres">
      <select
        name="genre"
        id="select-genres"
        v-model="genreFilter"
        @change="genreChange"
      >
        <option value="all">Select Genre</option>
        <option v-for="genre in genresList" :key="genre" :value="genre">
          {{ genre }}
        </option>
      </select>
    </label>
  </div>
</template>

<script>

export default {
  name: 'HeaderPage',
  props: {
    genresList: Array,
  },
  data() {
    return {
      genreFilter: 'all',
    };
  },
  methods: {
    genreChange() {
      this.$emit('changedGenre', this.genreFilter);
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
