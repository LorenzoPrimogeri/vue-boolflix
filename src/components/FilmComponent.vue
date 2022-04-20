<template>
  <div>
    <div v-for="film in arrayFilm" :key="film.id">
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
    arrayFilm: Array,
  },
  computed: {
    indentyCountry() {
      const filter = this.arrayFilm.filter((item) => {
        return;
      });
      return filter;
    },
  },
  methods: {},
};
</script>

<style>
</style>