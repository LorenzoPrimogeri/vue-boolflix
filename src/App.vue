<template>
  <div id="app">
    <HeaderComponent @search="searchContents" />
    <MainComponent :films="films" :series="series" />
    <NoContent :films="films" />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
import NoContent from "./components/NoContent.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    MainComponent,
    HeaderComponent,
    NoContent,
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
    axiosfunction(searchPhase, inpuText, array) {
      const params = {
        query: inpuText,
        api_key: this.apiKey,
        langugage: "it-IT",
      };
      axios
        .get(this.apiUrl + searchPhase, { params })
        .then((response) => {
          console.log(response.data);
          array.push(...response.data.results);
        })
        .catch((error) => {
          console.log(error);
        });
    },
    searchContents(inpuText) {
      if (inpuText.length > 0) {
        this.films = [];
        this.series = [];
        this.axiosfunction("movie", inpuText, this.films);
        this.axiosfunction("tv", inpuText, this.series);
      }
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.c-white {
  color: white;
}
.c-yellow {
  color: yellow;
}
.bg-black {
  background-color: black;
}
ul {
  list-style-type: none;
}
p {
  margin: 0;
}
body {
  font-family: "Netflix Sans", "Helvetica Neue", Helvetica, Arial, sans-serif;
}
</style>
