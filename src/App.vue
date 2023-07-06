<template>
  <div id="app">
    <div class="logo-nav">
      <img alt="Vue logo" src="./assets/logo.png" width="300" />
      <div class="logo-text">The Mars Files</div>
      <img src="./assets/marsLogo.gif" width="80" />
    </div>
    <el-container style="min-height: 800px; border: 1px solid #eee">
      <el-aside width="300px" style="background-color: #ff9d6f; padding: 12px">
        <div class="aside-title">CHOOSE YOUR VIEW !</div>
        <div class="aside-action">
          <el-button @click="chooseView('curiosity')">Curiosity</el-button>
          <el-button @click="chooseView('opportunity')">Opportunity</el-button>
          <el-button @click="chooseView('spirit')">Spirit</el-button>
        </div>
        <div><img src="./assets/buzz.gif" alt="" width="300" /></div>
      </el-aside>
      <el-container>
        <el-main>
          <ImagesContent ref="imagesContentRef" />
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import ImagesContent from "./components/ImagesContent.vue";

export default {
  name: "App",
  components: {
    ImagesContent,
  },
  methods: {
    chooseView(rover) {
      this.$refs.imagesContentRef.selectRover(rover);
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap");

.logo-nav {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 24px;
}

.logo-text {
  font-family: "Bebas Neue", sans-serif;
  font-size: 80px;
  color: #000;
}

.aside-title {
  font-family: "Bebas Neue", sans-serif;
  font-size: 64px;
}

.aside-action {
  display: flex;
}

button {
  font-family: "Bebas Neue", sans-serif;
}
</style>
