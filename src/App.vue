<template>
  <div id="app">
    <div :class="{ blur: isHoverStart }">
      <div class="hand"><img src="./assets/hand-up.png" /></div>
      <div class="star"><img src="./assets/falling-star.png" /></div>
      <div class="clock"><img src="./assets/clock.png" /></div>
      <div class="background" />
    </div>
    <StartButton
      @mouseover="handleHOverStart(true)"
      @mouseleave="handleHOverStart(false)"
    />
  </div>
</template>

<script>
import StartButton from "./components/StartButton.vue";
export default {
  name: "App",
  components: { StartButton },
  data() {
    return {
      isHoverStart: false,
    };
  },
  methods: {
    handleHOverStart(boolean) {
      this.isHoverStart = boolean;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "./assets/scss/main.css";
#app {
  width: 100vw;
  height: 100vh;

  position: relative;

  .blur {
    filter: blur(1px);
    * {
      filter: blur(1px);
    }
  }

  .background {
    height: 102vh;
    width: 102vw;
    transform: translate(-1vw, -1vh);
    background: url("./assets/background.png");
    background-size: cover;
  }

  .hand {
    width: 78px;
    height: 78px;
    position: fixed;
    top: 24px;
    right: 24px;
    background: #000000;
    transition: height 1s ease 0s, width 1s ease 0s;
    z-index: 2;
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
    z-index: 2;
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
    z-index: 2;
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
