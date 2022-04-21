<template>
  <div>
    <FilmComponent :films="films" />
    <SerieComponent :series="series" />
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
    films: Array,
    series: Array,
  },
};
</script>

<style scoped>
</style>
foglio di mezzo di contrasto per la tac, me lo potete mandare via email