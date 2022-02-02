<template>
  <div class="mask" @click.self="toggleModal">
    <div class="modal"><slot /></div>
  </div>
</template>

<script>
export default {
  methods: {
    toggleModal() {
      this.$emit("close");
    },
  },
};
</script>

<style lang="scss" scoped>
.mask {
  z-index: 999;
  position: fixed;
  top: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.5);
  width: 100vw;
  height: 100vh;
}
.modal {
  background: #000;
  width: calc(100vw - 40px);
  //   height: calc(100vh - 80px);
  top: 20px;
  left: 40px;
  position: fixed;
}
</style>
