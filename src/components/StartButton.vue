<template>
  <div
    class="start"
    @mouseover="handleMouseOver"
    @mouseleave="handleMouseLeave"
  >
    START
  </div>
</template>

<script>
export default {
  methods: {
    handleMouseOver() {
      this.$emit("mouseover");
    },
    handleMouseLeave() {
      this.$emit("mouseleave");
    },
  },
};
</script>

<style lang="scss" scoped>
@import url("http://fonts.cdnfonts.com/css/racing-sans-one");

.start {
  font-family: Racing Sans One;
  font-size: 36px;
  line-height: 45px;
  color: #fff;
  border: 7px solid #fff;
  box-sizing: border-box;
  border-radius: 30px;
  width: fit-content;
  padding: 5px 30px;
  position: absolute;
  top: 70vh;
  left: 50vw;
  transform: translate(-50%, 0);
  // z-index: 99;
  background: rgba(255, 255, 255, 0.23);
  &:hover {
    cursor: pointer;
  }
}
</style>
