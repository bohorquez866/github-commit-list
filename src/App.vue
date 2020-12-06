<template>
  <home msg="Jesus Commit History" />
</template>

<script>
import home from "./components/home.vue";

export default {
  name: "App",
  components: {
    home
  }
};
</script>

<style lang="scss">
@import "src/assets/scss/main.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
