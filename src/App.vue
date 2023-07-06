<template>
  <div id="app">
    <div class="logo-nav" id="tothetop">
      <img src="./assets/logo.png" alt="Vue logo" width="300" />
      <div class="logo-text">The Mars Files</div>
      <img src="./assets/marsLogo.gif" width="80" />
    </div>
    <el-container style="min-height: 800px; border: 1px solid #eee">
      <!-- faire des classes -->
      <SideBar @choose-view="chooseView" />
      <el-container>
        <el-main>
          <ImagesContent ref="imagesContentRef" />
        </el-main>
      </el-container>
      <div class="goToTheTop">
        <a href="#tothetop">
          <div class="blockToTheTop">
            <img src="./assets/tothetop.gif" width="100" height="100" />
            <span>To infinity and beyond</span>
          </div>
        </a>
      </div>
    </el-container>
  </div>
</template>

<script>
import ImagesContent from "./components/ImagesContent.vue";
import SideBar from "./layouts/SideBar.vue";

export default {
  name: "App",
  components: {
    ImagesContent,
    SideBar,
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

.goToTheTop {
  position: fixed;
  bottom: 30px;
  right: 30px;
  z-index: 9999;
}

.blockToTheTop {
  display: flex;
  flex-direction: column;
  align-items: center;
}

span {
  font-family: "Bebas Neue", sans-serif;
  font-size: 16px;
  color: #000;
}

a {
  text-decoration: none;
}
</style>
