<template>
  <div class="about">
    <section>
      <div class="about__section">
        <div class="about__section_title">ABOUT</div>
        <div class="about__section_content">
          《叛徒夏油可能的回憶錄》<br />
          文字腳本｜和樹<br />
          ＣＧ繪製｜和樹<br />
          <br />
          《2022夏油傑生誕祭：オマエもいる》<br />
          共同主題｜同居日常<br />
          抽籤題目｜請求<br />
          活動發起｜PLURK＠gsgs20171224<br />
          #2022夏油傑誕生祭 #オマエもいる<br />
          #夏五24HR創作活動<br />
        </div>
      </div>
      <div class="about__section second">
        <div class="about__section_title">SPECIAL THANKS</div>
        <div class="about__section_content">
          網頁工程｜生菜 ( github / v61265 )<br />
          技術諮詢｜全糖
        </div>
      </div>
    </section>
    <img src="../assets/title.png" />
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
  @media (min-width: 1200px) {
    // padding: 50px 70px;
    display: flex;
    text-align: start;
    justify-content: space-between;
  }

  .second {
    margin-top: 36px;
  }

  img {
    display: none;
    @media (min-width: 1200px) {
      display: block;
    }
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
        font-size: 16px;
        line-height: 20px;
      }
    }
  }
}
</style>
