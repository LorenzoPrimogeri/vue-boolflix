<template>
  <div>
    <div v-for="film in arraySerie" :key="film.id">
      <p>{{ film.title }}</p>
      <p>{{ film.original_title }}</p>
      <p>{{ film.original_language }}</p>
      <p>{{ film.vote_average }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmComponent",
  props: {
    arraySerie: Array,
  },
};
</script>

<style>
</style>