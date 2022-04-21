<template>
  <div>
    <div v-for="film in arrayFilm" :key="film.id">
      <p>{{ film.title }}</p>
      <p>{{ film.original_title }}</p>
      <img
        :src="getFlag(film.original_language)"
        :alt="film.original_language"
      />
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
  methods: {
    getFlag(langugage) {
      if (langugage == "en") {
        return "https://www.kidlink.org/icons/f0-uk.gif";
      }
      if (langugage == "zh") {
        return "https://www.kidlink.org/icons/f0-hk.gif";
      }
      if (langugage == "ml") {
        return "https://www.kidlink.org/icons/f0-my.gif";
      }
      if (langugage == "da") {
        return "https://www.kidlink.org/icons/f0-dk.gif";
      }
      return "https://www.kidlink.org/icons/f0-" + langugage + ".gif";
    },
  },
};
</script>

<style>
</style>