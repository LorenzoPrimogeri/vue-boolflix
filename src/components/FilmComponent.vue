<template>
  <div>
    <div v-for="film in arrayFilm" :key="film.id">
      <p>{{ film.title }}</p>
      <p>{{ film.original_title }}</p>
      <img
        :src="'../assets/img/' + film.original_language + '.png'"
        :alt="film.original_language"
      />
      <img src="../assets/img/it.png" alt="">
      <p>{{ film.vote_average }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmComponent",
  props: {
    arrayFilm: Array,
  },
};
</script>

<style>
</style>