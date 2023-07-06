<template>
  <div class="container">
    <div class="section">
      <div v-for="x in 10" :key="x">
        <ImageCard />
      </div>
    </div>
  </div>
</template>

<script>
import ImageCard from "./ImageCard.vue";
//import { marsRoverService } from '@/services';
export default {
  name: "ImagesContent",
  components: { ImageCard },
  data() {
    return {
      /* nameOfRover: "curiosity",
      pageNumber: 1, */
    };
  },
  mounted() {
    this.fetchData();
  },

  methods: {
    async fetchData() {
      /* try {
        const response = await marsRoverService.getMarsRover(this.nameOfRover, this.pageNumber);
        console.log(response.data);
      } catch (error) {
        console.error("An error occurred:", error);
      } */
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  display: flex;
  flex-direction: column;
}

.title {
  margin-bottom: 64px;
}
.section {
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  gap: 16px;
}
</style>
