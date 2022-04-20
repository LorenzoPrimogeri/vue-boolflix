<template>
  <div id="app">
    <HeaderComponent @search="searchContents" />
    <MainComponent :arrayFilm="arrayFilm" />
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
      arrayFilm: [],
    };
  },
  methods: {
    searchContents(inpuText) {
      const params = {
        query: inpuText,
        api_key: this.apiKey,
        langugage: "it-IT",
      };
      axios
        .get(this.apiUrl + "movie", { params })
        .then((response) => {
          this.arrayFilm = response.data.results;
          console.log(this.arrayFilm);
          return this.arrayFilm;
        })
        .catch((error) => {
          console.log(error);
        });
      console.log(inpuText);
    },
  },
};
</script>

<style lang="scss">
</style>
