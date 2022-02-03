<template>
  <div id="app">
    <div :class="{ blur: isHoverStart }">
      <div class="hand" id="intro" @click="setModal('intro')">
        <img v-show="introStatus === 'icon'" src="./assets/hand-up.png" />
        <Intro v-show="introStatus === 'content' && !this.isMobile" />
      </div>
      <div class="star" id="about" @click="setModal('about')">
        <img v-show="aboutStatus === 'icon'" src="./assets/falling-star.png" />
        <About v-show="aboutStatus === 'content' && !this.isMobile" />
      </div>
      <div class="clock" id="time" @click="setModal('time')">
        <img v-show="timeStatus === 'icon'" src="./assets/clock.png" />
        <Time
          v-show="timeStatus === 'content' && !this.isMobile"
          :time="time"
        />
      </div>
      <div class="background" />
    </div>
    <Modal v-show="openModal" @close="setModal(null)">
      <Intro v-show="openModal === 'intro'" />
      <About v-show="openModal === 'about'" />
      <Time v-show="openModal === 'time'" :time="time" />
      <Hint v-show="openModal === 'start'" />
    </Modal>
    <StartButton
      @mouseover="handleHOverStart(true)"
      @mouseleave="handleHOverStart(false)"
      @click.native="setModal('start')"
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
import Hint from "./components/Hint.vue";

export default {
  name: "App",
  components: { StartButton, Intro, Modal, About, Time, Hint },
  data() {
    return {
      isMobile: true,
      isHoverStart: false,
      openModal: null,
      introStatus: "icon",
      timeStatus: "icon",
      aboutStatus: "icon",
      duration: 0,
      introWidth: 0,
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
    this.$nextTick(() => {
      this.isMobile = window.innerWidth <= 768;
      window.addEventListener("resize", this.onResize);

      // 設定 hover 動畫顯示與消失
      const intro = document.getElementById("intro");
      const about = document.getElementById("about");
      const time = document.getElementById("time");

      // 動畫開始時什麼都不顯示
      intro.addEventListener(
        "transitionstart",
        () => (this.introStatus = null)
      );
      about.addEventListener(
        "transitionstart",
        () => (this.aboutStatus = null)
      );
      time.addEventListener("transitionstart", () => (this.timeStatus = null));

      // 動畫結束時各自顯示
      intro.addEventListener("transitionend", this.handleIntroEnd);
      about.addEventListener("transitionend", this.handleAboutEnd);
      time.addEventListener("transitionend", this.handleTimeEnd);
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
      if (
        this.introStatus === "content" ||
        this.aboutStatus === "content" ||
        this.timeStatus === "content"
      )
        return;
      this.isHoverStart = boolean;
    },
    setModal(value) {
      if (!this.isMobile && value !== "start") return (this.openModal = null);
      this.openModal = value;
    },
    handleIntroEnd(e) {
      this.introStatus = e.target.clientHeight === 78 ? "icon" : "content";
    },
    handleAboutEnd(e) {
      this.aboutStatus = e.target.clientHeight === 78 ? "icon" : "content";
    },
    handleTimeEnd(e) {
      this.timeStatus = e.target.clientHeight === 78 ? "icon" : "content";
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
  background: #000;
  .blur {
    animation: image_blur 5s;
    animation-fill-mode: forwards;
    * {
      animation: image_blur 5s;
      animation-fill-mode: forwards;
    }
  }

  @keyframes image_blur {
    0% {
      filter: blur(0px);
    }
    50% {
      filter: blur(2px);
    }
    100% {
      filter: blur(4px);
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
      transition: display 1s ease 0s;
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
        height: calc(100vh - 80px);
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
