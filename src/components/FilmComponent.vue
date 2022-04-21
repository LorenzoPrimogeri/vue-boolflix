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
            @error="setAltImg"
          />
        </div>
        <p>{{ film.title }}</p>
        <div>
          <img
            :src="getFlag(film.original_language)"
            :alt="film.original_language"
          />
        </div>
        <p class="c-white">
          <font-awesome-icon
            v-for="(star, index) in getValue(film.vote_average)"
            :key="index"
            icon="fa-solid fa-star"
            class="c-yellow"
          /><span>
            <font-awesome-icon
              v-for="(star, index) in getWhiteStar(film.vote_average)"
              :key="index"
              icon="fa-solid fa-star"
              class="c-white"
            />
          </span>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import img from "../assets/img/error.png";
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
      if (value >= 1 && value <= 2) {
        return 1;
      }
      if (value >= 2 && value <= 4) {
        return 2;
      }
      if (value >= 4 && value <= 6) {
        return 3;
      }
      if (value >= 6 && value <= 8) {
        return 4;
      }
      if (value >= 8 && value <= 10) {
        return 5;
      }
    },
    getWhiteStar(value) {
      let yellowstar = this.getValue(value);
      if (value == 0) {
        yellowstar = 0;
      }
      console.log(yellowstar);
      const result = 5 - yellowstar;
      console.log("il risultato è" + result);
      return result;
    },
    setAltImg(event) {
      event.target.src = img;
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