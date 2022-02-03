<template>
  <div class="hint">
    <div class="hint__section">
      <div class="hint__section_title">HINT</div>
      <div class="hint__section_content">
        請按照下列步驟開始遊戲：
        <ul>
          <li>
            1. <span class="link" @click="handleClick">點我</span> 進入 Facebook
            粉絲專頁。
          </li>
          <li>2. 私訊並按下「開始使用」。</li>
          <li>3. 祝您有美好的遊戲體驗～</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    handleClick() {
      window.open(
        "https://www.facebook.com/ThePossibleMemoirsOfATraitor",
        "_blank"
      );
    },
  },
};
</script>

<style lang="scss" scoped>
.hint {
  color: #fff;
  padding: 28px 10px;
  text-align: center;
  @media (min-width: 768px) {
    padding: 50px 70px;
    text-align: start;
  }

  &__section {
    @media (min-width: 768px) {
      flex: 1;
    }
    &_title {
      font-family: Racing Sans One;
      font-size: 24px;
      line-height: 30px;
      @media (min-width: 768px) {
        font-size: 42px;
        line-height: 48px;
      }
    }
    &_content {
      margin-top: 12px;
      font-size: 12px;
      line-height: 16px;
      @media (min-width: 768px) {
        margin-top: 16px;
        font-size: 20px;
        line-height: 28px;
      }
    }
  }

  .link {
    // text-decoration: underline;
    position: relative;
    &::before {
      content: "";
      position: absolute;
      left: 0;
      bottom: 2px;
      width: 50px;
      height: 8px;
      transform: skew(-12deg) translateX(-25%);
      background: #ff1f5e;
      opacity: 0.8;
      z-index: -1;
    }
    &:hover {
      cursor: pointer;
      font-weight: 500;
    }
  }
}
</style>
