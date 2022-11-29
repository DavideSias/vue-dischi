<template>
  <div>
    <div class="container p-5" v-if="filteredSongs">
      <div class="row row-cols-lg-5 row-cols-md-3 row-cols-sm-2 g-4">
        <card-content
          v-for="song in filteredSongs"
          :key="song.title"
          :img-url="song.poster"
          :title="song.title"
          :author="song.author"
          :year="song.year"
        />
      </div>
    </div>
    <div v-else>Loading, please wait...</div>
  </div>
</template>

<script>
import axios from 'axios';
import CardContent from './CardContent.vue';

export default {
  name: 'MainPage',
  components: {
    CardContent,
  },
  data() {
    return {
      arrSongs: null,
      urlApi: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        this.arrSongs = axiosResponse.data.response;
      });
  },
  computed: {
    filteredSongs() {
      return this.arrSongs.filter((newValue) => newValue.genre === this.selectedValue);
    },
  },
  props: {
    selectedValue: String,
  },
};
</script>

<style lang="scss" scoped>
</style>
