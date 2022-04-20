<template>
  <div>
    <div>
      <input
        type="text"
        placeholder="Search"
        v-model="inpuText"
        @keyup.enter="$emit('search', inpuText)"
      />
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
</style>