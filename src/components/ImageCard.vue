<template>
  <img :src="sourceImg" alt="image_planet_mars" width="300" />
</template>

<script>
export default {
  name: "ImageCard",
  props: {
    sourceImg: {
      type: String,
      default: "https://placehold.co/300x300/png",
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  cursor: pointer;
}
</style>
