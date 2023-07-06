<template>
  <img :src="sourceImg" alt="image_planet_mars" width="300" />
</template>

<script>
export default {
  name: "ImageCard",
  props: {
    sourceImg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
img {
  cursor: pointer;
}
</style>
