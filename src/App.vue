<template>
  <div id="app">
    <HeaderComponent @search="searchContents" />
    <MainComponent :arrayFilm="films" :arraySerie="series" />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    MainComponent,
    HeaderComponent,
  },
  data() {
    return {
      apiKey: "2f328d6399188dd310a23b37fa808671",
      apiUrl: "https://api.themoviedb.org/3/search/",
      films: [],
      series: [],
    };
  },
  methods: {
    movieOrSerie(search) {
      return this.searchContents("", search);
    },
    searchContents(inpuText) {
      if (inpuText.length > 0) {
        const params = {
          query: inpuText,
          api_key: this.apiKey,
          langugage: "it-IT",
        };
        axios
          .get(this.apiUrl + "movie", { params })
          .then((response) => {
            console.log(response.data);
            this.films = response.data.results;
          })
          .catch((error) => {
            console.log(error);
          });
        axios
          .get(this.apiUrl + "tv", { params })
          .then((response) => {
            console.log(response.data);
            this.series = response.data.results;
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
};
</script>

<style lang="scss">
div {
  text-align: center;
}
</style>
