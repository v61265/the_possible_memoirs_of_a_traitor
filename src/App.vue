<template>
  <div id="app">
    <div class="top" />
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
};
</script>

<style lang="scss" scoped>
@import "./assets/scss/main.css";
#app {
  width: 100vw;
  height: 100vh;
  background: #dceeef;
  position: relative;

  .top {
    width: 78px;
    height: 78px;
    position: fixed;
    top: 24px;
    right: 24px;
    background: #000000;
    transition: height 1s ease 0s, width 1s ease 0s;
    &:hover {
      width: 300px;
      height: 300px;
    }
  }
}
</style>
