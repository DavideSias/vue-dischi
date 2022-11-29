<template>
  <div>
    <label for="genre">
      <select @change="$emit('change', value)" name="genre" id="genre">
        <option value="none">Seleziona un genere</option>
        <option value="rock">rock</option>
        <option value="metal">metal</option>
        <option value="pop">pop</option>
      </select>
    </label>
  </div>
</template>

<script>
// import axios from 'axios';

export default {
  name: 'SelectGenre',
  data() {
    return {
      value: 'none',
    };
  },
};
</script>

<style>

</style>
