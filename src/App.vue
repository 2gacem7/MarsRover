<template>
  <div id="app">
    <div class="logo-nav">
      <img alt="Vue logo" src="./assets/logo.png" width="300" />
      <div class="logo-text">The Mars Files</div>
    </div>
    <el-container style="min-height: 800px; border: 1px solid #eee">
      <el-aside width="300px" style="background-color: #ff9d6f; padding: 12px">
        <div class="aside-title">CHOOSE YOUR VIEW !</div>
        <div class="aside-action">
          <el-button>Curiosity</el-button>
          <el-button>Opportunity</el-button>
          <el-button>Spirit</el-button>
        </div>
      </el-aside>
      <el-container>
        <el-header style="text-align: right; font-size: 12px">
          <img src="./assets/marsLogo.gif" width="48" />
        </el-header>
        <el-main>
          <ImagesContent />
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
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap");

.logo-nav {
  display: flex;
  align-items: center;
  justify-content: center;
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
