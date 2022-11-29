<template>
  <div>
    <div class="card col text-center p-2 bg_color">
      <img :src="imgUrl" class="card-img-top" :alt="title">
      <div class="card-body">
        <h5 class="card-title">{{ title }}</h5>
        <p class="card-text sub_text">{{ author }}</p>
        <p class="card-text sub_text">{{ year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CardContent',
  props: {
    imgUrl: String,
    title: String,
    author: String,
    year: String,

    // alternativa in cui dichiariamo la props come oggetto intero
    // songInfo: Object,
  },
};
</script>

<style lang="scss" scoped>
  .bg_color{
    background-color: rgb(46, 58, 70);
    color: white;
    height: 100%;

    .sub_text{
      color: gray;
    }
  }
</style>
