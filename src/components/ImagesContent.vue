<template>
  <div class="container">
    <div class="section">
      <div v-for="item in items" :key="item.id">
        <ImageCard :sourceImg="item.img_src" />
      </div>
    </div>
  </div>
</template>

<script>
import ImageCard from "./ImageCard.vue";
import { marsRoverService } from "@/services";
export default {
  name: "ImagesContent",
  components: {
    ImageCard,
  },
  data() {
    return {
      nameOfRover: "curiosity",
      pageNumber: 1,
      items: [],
    };
  },
  mounted() {
    this.fetchData();
  },

  methods: {
    async fetchData() {
      try {
        const response = await marsRoverService.getMarsRover(
          this.nameOfRover,
          this.pageNumber
        );
        this.items = response.data.photos;
      } catch (error) {
        console.error("An error occurred:", error);
      }
    },
    selectRover(rover) {
      console.log(rover);
      this.nameOfRover = rover;
      console.log(rover);
      this.fetchData();
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
