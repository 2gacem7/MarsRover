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
      curiosityData: [],
      opportunityData: [],
      spiritData: [],
      isFetching: false,
    };
  },
  mounted() {
    this.fetchData();
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    async fetchData(rover) {
      try {
        this.isFetching = true;
        const response = await marsRoverService.getMarsRover(
          this.nameOfRover,
          this.pageNumber
        );
        const newData = response.data.photos;
        if (this.nameOfRover === "curiosity") {
          // Merging the new data with the old data in case of infinite scroll
          this.curiosityData = [...this.curiosityData, ...newData];
          this.items = this.curiosityData;
        } else if (rover === "opportunity") {
          // Merging the new data with the old data in case of infinite scroll
          this.opportunityData = [...this.opportunityData, ...newData];
          this.items = this.opportunityData;
        } else if (rover === "spirit") {
          // Merging the new data with the old data in case of infinite scroll
          this.spiritData = [...this.spiritData, ...newData];
          this.items = this.spiritData;
        }
        this.pageNumber++;
        this.isFetching = false;
      } catch (error) {
        console.error("An error occurred:", error);
        this.isFetching = false;
      }
    },
    selectRover(rover) {
      this.nameOfRover = rover;
      if (rover === "opportunity" && this.opportunityData.length > 0) {
        return (this.items = this.opportunityData);
      }
      if (rover === "curiosity" && this.curiosityData.length > 0) {
        return (this.items = this.curiosityData);
      }
      if (rover === "spirit" && this.spiritData.length > 0) {
        return (this.items = this.spiritData);
      }
      // Reset pageNumber
      this.pageNumber = 1;
      this.fetchData(rover);
    },
    handleScroll() {
      if (
        window.innerHeight + window.pageYOffset >=
        document.documentElement.offsetHeight - 500
      ) {
        if (!this.isFetching) {
          this.fetchData();
        }
      }
    },
  },
};
</script>

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
