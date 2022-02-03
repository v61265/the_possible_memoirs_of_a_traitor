<template>
  <div class="time">
    <div class="time__date">2 0 2 2 / 2 / 3</div>
    <div class="time__time">{{ time }}</div>
  </div>
</template>

<script>
export default {
  props: {
    time: {
      type: String,
      default: "19 : 00",
    },
  },
};
</script>

<style lang="scss" scoped>
.time {
  color: #fff;
  padding: 28px 10px;
  font-size: 34px;
  line-height: 43px;
  font-family: Racing Sans One;
  text-align: center;
  @media (min-width: 768px) {
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    height: 50vh;
    align-items: center;
    justify-content: center;
    padding: 50px 70px;
    text-align: start;
    font-size: 36px;
    line-height: 45px;
  }
  &__time {
    font-size: 64px;
    line-height: 81px;
    @media (min-width: 768px) {
      font-size: 114px;
      line-height: 144px;
    }
  }
}
</style>
