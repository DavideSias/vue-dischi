<template>
  <div>
    <div class="container p-5" v-if="arrSongs">
      <div class="row row-cols-lg-5 row-cols-md-3 row-cols-sm-2 g-4">
        <card-content
          v-for="song in arrDiscFiltered"
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
  props: {
    genreFilter: String,
  },
  computed: {
    arrGenres() {
      const arrGenres = [];
      /* questo if serve per controllare se l'array è pieno o vuoto,
      dato che abbiamo dichiarato l'array con null per aspettare
      di visualizzare i dati al caricamento della pagina */
      if (this.arrSongs) {
        this.arrSongs.forEach((objSong) => {
          if (!arrGenres.includes(objSong.genre)) {
            arrGenres.push(objSong.genre);
          }
        });
      }
      return arrGenres;
    },
    // nuova computed per l'array filtrato
    arrDiscFiltered() {
      if (this.genreFilter === 'all') {
        return this.arrSongs;
      }
      return this.arrSongs.filter((objDisc) => objDisc.genre === this.genreFilter);
    },
  },
  watch: {
    arrGenres(newValue, oldValue) {
      console.log(newValue, oldValue);
      this.$emit('genresReady', newValue);
    },
  },
  created() {
    axios.get(this.urlApi)
      .then((axiosResponse) => {
        this.arrSongs = axiosResponse.data.response;
      });
  },
};
</script>

<style lang="scss" scoped>
</style>
