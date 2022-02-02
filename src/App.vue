<template>
  <div id="app">
    <div :class="{ blur: isHoverStart }">
      <div class="hand" id="intro" @click="setModal('intro')">
        <img v-show="introStatus === 'icon'" src="./assets/hand-up.png" /><Intro
          v-show="introStatus === 'content' && !this.isMobile"
        />
      </div>
      <div
        class="star"
        v-show="aboutStatus === 'icon'"
        @click="setModal('about')"
      >
        <img src="./assets/falling-star.png" />
      </div>
      <div
        class="clock"
        v-show="timeStatus === 'icon'"
        @click="setModal('time')"
      >
        <img src="./assets/clock.png" />
      </div>
      <div class="background" />
    </div>
    <Modal v-show="openModal" @close="setModal(null)">
      <Intro v-show="openModal === 'intro'" />
      <About v-show="openModal === 'about'" />
      <Time v-show="openModal === 'time'" :time="time" />
    </Modal>
    <StartButton
      @mouseover="handleHOverStart(true)"
      @mouseleave="handleHOverStart(false)"
    />
  </div>
</template>

<script>
import moment from "moment";
import StartButton from "./components/StartButton.vue";
import Intro from "./components/Intro.vue";
import Modal from "./components/Modal.vue";
import About from "./components/About.vue";
import Time from "./components/Time.vue";

export default {
  name: "App",
  components: { StartButton, Intro, Modal, About, Time },
  data() {
    return {
      isMobile: true,
      isHoverStart: false,
      openModal: null,
      introStatus: "icon",
      timeStatus: "icon",
      aboutStatus: "icon",
      duration: 0,
    };
  },
  computed: {
    time() {
      var date = new Date("2022-02-03 19:00:00");
      var date_ts = date.getTime() + 1000 * this.duration;
      return moment(date_ts).format("HH : mm");
    },
  },
  mounted() {
    const hand = document.getElementsByClassName("hand")[0];
    console.log(hand);
    hand.addEventListener("animationstart", this.introListener);
    hand.addEventListener("animationend", this.introListener);
    this.$nextTick(() => {
      this.isMobile = window.innerWidth <= 768;
      window.addEventListener("resize", this.onResize);
    });
    setInterval(() => {
      this.duration++;
    }, 1000);
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.onResize);
  },
  methods: {
    onResize() {
      this.isMobile = window.innerWidth < 768;
    },
    handleHOverStart(boolean) {
      this.isHoverStart = boolean;
    },
    introListener(e) {
      console.log(e);
    },
    setModal(value) {
      if (!this.isMobile) return;
      this.openModal = value;
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
    height: 100vh;
    width: 100vw;
    background: url("./assets/background_sm.png");
    background-size: cover;
    background-position: center;
    @media (min-width: 768px) {
      background: url("./assets/background.png");
      background-size: cover;
      background-position: center;
    }
  }

  .hand {
    width: 78px;
    height: 78px;
    position: fixed;
    bottom: 24px;
    right: 50vw;
    background: #000000;
    transform: translate(50%, 0);
    z-index: 2;
    img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    @media (min-width: 768px) {
      transition: height 1s ease 0s, width 1s ease 0s;
      top: 24px;
      right: 24px;
      bottom: auto;
      transform: none;
      &:hover {
        width: calc(100vw - 160px);
        height: calc(100vh - 160px);
      }
    }
  }

  .star {
    width: 78px;
    height: 78px;
    position: fixed;
    bottom: 24px;
    left: 24px;
    background: #000000;
    z-index: 2;
    img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    @media (min-width: 768px) {
      transition: height 1s ease 0s, width 1s ease 0s;
      &:hover {
        width: calc(100vw - 160px);
        height: calc(100vh - 160px);
      }
    }
  }

  .clock {
    width: 78px;
    height: 78px;
    position: fixed;
    bottom: 24px;
    right: 24px;
    background: #000000;
    z-index: 2;
    img {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
    @media (min-width: 768px) {
      transition: height 1s ease 0s, width 1s ease 0s;
      &:hover {
        width: 50vw;
        height: 50vh;
      }
    }
  }
}
</style>
