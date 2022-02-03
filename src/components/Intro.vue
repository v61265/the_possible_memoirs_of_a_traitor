<template>
  <div class="intro">
    <div class="intro__section">
      <div class="intro__section_title">Equipment Requirements /</div>
      <div class="intro__section_content">
        本Chatbot遊戲使用Facebook的Messenger程式驅動。<br />
        若使用桌機、筆電開啟，請確保Facebook帳號登入。若使用手機、平板開啟，請確保已下載Messenger
        APP。
      </div>
    </div>
    <div class="intro__section">
      <div class="intro__section_title">Trouble Shooting /</div>
      <div class="intro__section_content">
        若尚未抵達結局，Chatbot便出現停止運作/未繼續跳出內容的狀況，可能是過多使用者同步使用、導致Chatbot漏接訊息。請回到上一個「選擇分支」，按下所選按鍵，Chatbot即可重新接收指令，再次開始運作。
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.intro {
  color: #fff;
  padding: 28px 10px;
  text-align: center;
  @media (min-width: 1200px) {
    text-align: start;
    padding: 50px 70px;
  }

  & > div + div {
    margin-top: 36px;
  }

  &__section {
    &_title {
      font-family: Racing Sans One;
      font-size: 24px;
      line-height: 30px;
      @media (min-width: 1200px) {
        font-size: 36px;
        line-height: 45px;
      }
    }
    &_content {
      margin-top: 12px;
      font-size: 12px;
      line-height: 16px;
      @media (min-width: 1200px) {
        margin-top: 16px;
        font-size: 20px;
        line-height: 29px;
      }
    }
  }
}
</style>
