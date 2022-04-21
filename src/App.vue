<template>
  <div id="app">
    <HeaderComponent @search="searchContents" />
    <MainComponent :films="films" :series="series" />
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
    axiosfunction(searchPhase, inpuText) {
      const params = {
        query: inpuText,
        api_key: this.apiKey,
        langugage: "it-IT",
      };
      axios
        .get(this.apiUrl + searchPhase, { params })
        .then((response) => {
          console.log(response.data);
          return response.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    searchContents(inpuText) {
      if (inpuText.length > 0) {
        this.films = this.axiosfunction("movie", inpuText);
        this.series = this.axiosfunction("tv", inpuText);
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
