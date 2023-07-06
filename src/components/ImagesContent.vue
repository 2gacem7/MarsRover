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
      if (rover) this.nameOfRover = rover;
      try {
        this.isFetching = true;
        const response = await marsRoverService.getMarsRover(
          this.nameOfRover,
          this.pageNumber
        );
        const newData = response.data.photos;
        this.addNewData(newData);
        this.isFetching = false;
      } catch (error) {
        console.error("An error occurred:", error);
        this.isFetching = false;
      }
    },

    addNewData(newData) {
      if (this.nameOfRover === "curiosity") {
        // Merging the new data with the old
        this.curiosityData = [...this.curiosityData, ...newData];
        this.items = this.curiosityData;
      } else if (this.nameOfRover === "opportunity") {
        this.opportunityData = [...this.opportunityData, ...newData];
        this.items = this.opportunityData;
      } else if (this.nameOfRover === "spirit") {
        this.spiritData = [...this.spiritData, ...newData];
        this.items = this.spiritData;
      }
      this.pageNumber++;
    },

    selectRover(rover) {
      this.nameOfRover = rover;
      if (
        this.nameOfRover === "opportunity" &&
        this.opportunityData.length > 0
      ) {
        return (this.items = this.opportunityData);
      }
      if (this.nameOfRover === "curiosity" && this.curiosityData.length > 0) {
        return (this.items = this.curiosityData);
      }
      if (this.nameOfRover === "spirit" && this.spiritData.length > 0) {
        return (this.items = this.spiritData);
      }
      // Reset pageNumber
      this.pageNumber = 1;
      this.fetchData(this.nameOfRover);
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
