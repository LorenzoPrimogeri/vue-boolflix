<template>
  <div>
    <div v-if="films.length <= 0" class="container-fluid">
      <div class="row align-items-center justify-content-center">
        <div class="col">
          <h1 class="c-white text-center">Search A Movie!</h1>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "NoContent",
  props: {
    films: Array,
  },
};
</script>

<style scoped>
.row {
  min-height: calc(100vh - 80px);
  background-color: black;
}
</style>