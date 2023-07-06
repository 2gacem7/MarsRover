<template>
  <div>
    <el-aside
      width="300px"
      style="background-color: #ff9d6f; padding: 12px; height: 100%"
    >
      <div class="aside-title">CHOOSE YOUR ROVERS !</div>
      <div class="aside-action">
        <el-button @click="chooseFilter('curiosity')">Curiosity</el-button>
        <el-button @click="chooseFilter('opportunity')">Opportunity</el-button>
        <el-button @click="chooseFilter('spirit')">Spirit</el-button>
      </div>
      <div><img src="../assets/buzz.gif" alt="" width="280" /></div>
    </el-aside>
  </div>
</template>

<script>
export default {
  name: "SideBar",
  methods: {
    chooseFilter(value) {
      this.$emit("choose-view", value);
    },
  },
};
</script>

<style>
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
