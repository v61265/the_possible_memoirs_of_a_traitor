<template>
  <div class="about">
    <div class="about__section">
      <div class="about__section_title">ABOUT</div>
      <div class="about__section_content">
        《他們在結婚的前一天爆炸》<br />
        文字腳本｜和樹<br />
        ＣＧ繪製｜和樹<br />
        <br /><br />

        共同主題｜結婚<br />
        活動發起｜PLURK＠teatime725<br />
        #週日夏五茶 #夏油傑2022生誕祭<br />
        #夏油溫泉旅館自助餐<br />
      </div>
    </div>
    <div class="about__section">
      <div class="about__section_title">SPECIAL THANKS</div>
      <div class="about__section_content">
        網頁工程｜生菜 ( github / v61265 )<br />
        技術諮詢｜全糖
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.about {
  color: #fff;
  padding: 28px 10px;
  text-align: center;
  @media (min-width: 768px) {
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
      @media (min-width: 768px) {
        font-size: 36px;
        line-height: 45px;
      }
    }
    &_content {
      margin-top: 12px;
      font-size: 12px;
      line-height: 16px;

      @media (min-width: 768px) {
        margin-top: 16px;
        font-size: 20px;
        line-height: 29px;
      }
    }
  }
}
</style>
