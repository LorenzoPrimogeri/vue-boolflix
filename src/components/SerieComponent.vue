<template>
  <div class="container-fluid bg-black">
    <div v-if="series.length > 0">
      <h1 class="text-center c-white">Serie Tv</h1>
    </div>
    <div class="row">
      <div v-for="serie in series" :key="serie.id" class="col-3">
        <p>{{ serie.title }}</p>
        
        <p>{{ serie.original_title }}</p>
        <img
          :src="getFlag(serie.original_language)"
          :alt="serie.original_language"
        />
        <p>{{ serie.vote_average }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmComponent",
  props: {
    series: Array,
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