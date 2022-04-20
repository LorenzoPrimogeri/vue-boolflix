<template>
  <div>
    <FilmComponent :arrayFilm="arrayFilm" />
    <SerieComponent :arraySerie="arraySerie" />
  </div>
</template>

<script>
import FilmComponent from "./FilmComponent.vue";
import SerieComponent from "./SerieComponent.vue";
export default {
  name: "MainComponent",
  components: {
    FilmComponent,
    SerieComponent,
  },
  props: {
    arrayFilm: Array,
    arraySerie: Array,
  },
};
</script>

<style scoped>
</style>