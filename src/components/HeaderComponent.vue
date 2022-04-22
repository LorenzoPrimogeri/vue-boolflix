<template>
  <div class="container-fluid">
    <div class="header row bg-black">
      <div class="col-8 d-flex align-items-center">
        <div>
          <img src="../assets/img/netflixLogo.svg" alt="NetflixLogo" />
        </div>
        <div>
          <ul class="c-white">
            <li>Home</li>
            <li>Serie Tv</li>
            <li>Film</li>
            <li>Nuovi e popolari</li>
            <li>La mia lista</li>
          </ul>
        </div>
      </div>
      <div class="col-4 d-flex align-items-center c-white justify-content-end">
        <div>
          <input
            type="text"
            placeholder="Search"
            v-model="inpuText"
            @keyup.enter="$emit('search', inpuText)"
          />
        </div>
        <div>
          <img src="../assets/img/magnifying-glass-solid.svg" alt="glass" />
        </div>
        <div>
          <img src="../assets/img/bell-solid.svg" alt="bell" />
        </div>

        <div>
          <img src="../assets/img/ProfilePhoto.svg" alt="ProfilePhoto" />
        </div>
        <div>
          <img src="../assets/img/angle-down-solid.svg" alt="AngleDown" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderComponent",
  data() {
    return {
      inpuText: "",
    };
  },
};
</script>

<style scoped>
.header {
  height: 80px;
}
img[alt="NetflixLogo"] {
  width: 130px;
}
img[alt="ProfilePhoto"] {
  width: 30px;
}
img {
  width: 20px;
  margin: 0px 10px;
}
ul li {
  display: inline-block;
  padding: 10px 10px;
}
li:hover {
  color: grey;
}
ul,
p {
  padding: 0;
  margin: 0 !important;
}
</style>