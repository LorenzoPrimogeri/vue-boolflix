<template>
  <div class="container-fluid bg-black">
    <div v-if="films.length > 0">
      <h1 class="text-center c-white">Film</h1>
    </div>
    <div class="row gy-2 gx-4 c-white">
      <div v-for="film in films" :key="film.id" class="col-3 lp-card">
        <div class="w-100">
          <img
            :src="getImage(film.backdrop_path)"
            :alt="film.title"
            class="card-image"
          />
        </div>
        <p>{{ film.title }}</p>
        <div>
          <img
            :src="getFlag(film.original_language)"
            :alt="film.original_language"
          />
        </div>
        <p>{{ getValue(film.vote_average) }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmComponent",
  props: {
    films: Array,
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
    getImage(lastpath) {
      return "http://image.tmdb.org/t/p/w500/" + lastpath;
    },
    getValue(value) {
      if (value >= 1) {
        return "funziona";
      }
    },
  },
};
</script>

<style scoped>
.card-image {
  width: 100%;
}
.lp-card {
  border: 1px solid black;
}
</style>