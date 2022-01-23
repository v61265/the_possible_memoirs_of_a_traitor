<template>
  <div id="app">
    <div class="hand"><img src="./assets/hand-up.png" /></div>
    <div class="star"><img src="./assets/falling-star.png" /></div>
    <div class="clock"><img src="./assets/clock.png" /></div>
    <StartButton />
  </div>
</template>

<script>
import StartButton from "./components/StartButton.vue";
export default {
  name: "App",
  components: { StartButton },
};
</script>

<style lang="scss" scoped>
@import "./assets/scss/main.css";
#app {
  width: 100vw;
  height: 100vh;
  background: #dceeef;
  position: relative;

  .hand {
    width: 78px;
    height: 78px;
    position: fixed;
    top: 24px;
    right: 24px;
    background: #000000;
    transition: height 1s ease 0s, width 1s ease 0s;
    &:hover {
      width: calc(100vw - 160px);
      height: calc(100vh - 160px);
    }
    img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }

  .star {
    width: 78px;
    height: 78px;
    position: fixed;
    bottom: 24px;
    left: 24px;
    background: #000000;
    transition: height 1s ease 0s, width 1s ease 0s;
    &:hover {
      width: calc(100vw - 160px);
      height: calc(100vh - 160px);
    }
    img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }

  .clock {
    width: 78px;
    height: 78px;
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: #000000;
    transition: height 1s ease 0s, width 1s ease 0s;
    &:hover {
      width: 50vw;
      height: 50vh;
    }
    img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }
}
</style>
