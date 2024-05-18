<template>
  <v-stepper alt-labels class="elevation-0 transparent" v-model="e1">
    <v-stepper-header class="elevation-0">
      <v-stepper-step :complete="e1 > 1" step="1">制限時間の設定</v-stepper-step>
      <v-divider :class="e1 > 1 ? 'stepped-line' : ''"></v-divider>
      <v-stepper-step :complete="e1 > 2" step="2">出題タイトルの設定</v-stepper-step>
      <v-divider :class="e1 > 2 ? 'stepped-line' : ''"></v-divider>
      <v-stepper-step :complete="e1 > 3" step="3">出題クイズの設定</v-stepper-step>
      <v-divider :class="e1 > 3 ? 'stepped-line' : ''"></v-divider>
      <v-stepper-step step="4">最終確認</v-stepper-step>
    </v-stepper-header>
    <v-stepper-items>
      <v-stepper-content step="1">
        <v-container class="align-center d-flex elevation-0 justify-center my-12 transparent" height="200px">
          <v-row class="radioGroup">
            <div class="selectItem">
              <div class="bigRadio" :class="{'selected':this.isSelected==30, 'hovered':this.isHovered}" @click="isSelect(30)" @mouseover="onHover" @mouseleave="offHover"></div>
              <p class="selectText">30秒</p>
            </div>
            <div class="selectItem">
              <div class="bigRadio" :class="{'selected':this.isSelected==60, 'hovered':this.isHovered}" @click="isSelect(60)" @mouseover="onHover" @mouseleave="offHover"></div>
              <p class="selectText">60秒</p>
            </div>
            <div class="selectItem">
              <div class="bigRadio" :class="{'selected':this.isSelected==90, 'hovered':this.isHovered}" @click="isSelect(90)" @mouseover="onHover" @mouseleave="offHover"></div>
              <p class="selectText">90秒</p>
            </div>
          </v-row>
        </v-container>
        <v-btn class="stepBtn" @click="e1 = 2">進む</v-btn>
      </v-stepper-content>
      <v-stepper-content step="2">
        <v-container class="align-center d-flex elevation-0 justify-center my-12 transparent" height="200px">
          <div class="quizTitle">
            <v-card class="py-6 settingBox" outlined tile>
              <div class="textItem">タイトル</div>
              <div class="textBox">
                <input type="text" class="titleBox" v-model.trim="quizTitle" maxlength="20">
              </div>
              <div class="textCount">{{quizTitle.length}} / 20</div>
            </v-card>
          </div>
        </v-container>
        <v-btn class="stepBtn" text @click="e1 = 1">戻る</v-btn>
        <v-btn class="stepBtn" @click="e1 = 3" :disabled="this.quizTitle == ''" :class="{'disabled':this.quizTitle == ''}">進む</v-btn>
      </v-stepper-content>
    </v-stepper-items>
  </v-stepper>
</template>
<script>
export default {
  data() {
    return{
      e1: 1,
      isSelected: 30,
      isHovered: false,
      quizTitle: '',
    }
  },
  methods: {
    isSelect(n) {
      this.isSelected = n;
    },
    onHover() {
      this.isHovered = true;
    },
    offHover() {
      this.isHovered = false;
    }
  }
}
</script>
<style lang="scss">
  .v-stepper {
    margin: 40px auto;
    max-width: 1000px;
  }
  /* ステップステータス */
  .v-stepper .v-stepper__step {
    flex-basis: 250px !important;
  }
  .v-stepper .v-stepper__step .v-stepper__step__step {
    background: transparent !important;
    color: #000 !important;
    font-size: 2rem;
    font-weight: bold;
    height: 32px !important;
    opacity: .38;
    width: 32px !important;
  }
  .v-stepper .v-stepper__step .v-stepper__label {
    color: #000 !important;
    font-size: 1.2rem;
    opacity: .45;
  }
  .v-stepper .v-stepper__step--active .v-stepper__step__step {
    color: #f4d099 !important;
    opacity: 1;
    text-shadow: 0 0 5px #e00c1b;
  }
  .v-stepper .v-stepper__step--active .v-stepper__label {
    color: #f4d099 !important;
    font-size: 1.2rem;
    opacity: 1;
    text-shadow: 0 0 5px #e00c1b !important;
  }
  .v-stepper .v-divider {
    border-width: 1px;
  }
  .v-stepper .stepped-line {
    border-color: #f4d099 !important;
    box-shadow: 0 0 5px #e00c1b;
    opacity: 1;
  }
  /* メインコンテンツ */
  .v-stepper .v-stepper__content {
    padding: 0;
  }
  /* ステップ1 制限時間の設定 */
  .v-stepper .v-stepper__content .radioGroup {
    display: flex;
    justify-content: center;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem {
    width: 150px;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .bigRadio {
    border: 4px solid #000;
    border-radius: 50% !important;
    cursor: pointer;
    height: 50px;
    margin: auto;
    opacity: .45;
    position: relative;
    transition-duration: 0.5s;
    width: 50px;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .bigRadio:before {
    background: #000;
    border-radius: 50%;
    content: "";
    display: block;
    height: 30px;
    left: 50%;
    opacity: .45;
    position: absolute;
    top: 50%;
    transform: translate(-50%, -50%);
    transition-duration: 0.5s;
    width: 30px;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .bigRadio:hover {
    border-color: #f4d099;
    opacity: 1;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .bigRadio:hover:before {
    background: #f4d099;
    box-shadow: 0 0 10px #e00c1b;
    opacity: 1;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .selected {
    border-color: #f4d099;
    opacity: 1;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .selected:before {
    background: #f4d099;
    box-shadow: 0 0 10px #e00c1b;
    opacity: 1;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .hovered {
    border-color: #000;
    opacity: .45;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .hovered:before {
    background: #000;
    box-shadow: 0 0 10px #e00c1b;
    opacity: .45;
  }
  .v-stepper .v-stepper__content .radioGroup .selectItem .selectText {
    color: #fff;
    font-size: 1.6rem;
    margin: 5px;
  }
  /* ステップボタン */
  .v-stepper .stepBtn {
    background-color: transparent !important;
    background-image: linear-gradient(rgba(209, 190, 142, 0.4) 0%, #fef9d9 50%, #d1be8e 100%);
    border-radius: 18px;
    box-shadow: 0 4px 10px rgb(84 84 84 / 80%);
    height: 100% !important;
    margin: 10px;
    padding: 4px !important;
    width: 210px;
  }
  .v-stepper .stepBtn:hover {
    opacity: .6;
  }
  .v-stepper .stepBtn .v-btn__content {
    background: #970812 !important;
    border-radius: 10px;
    color: #fff;
    display: block;
    font-size: 1rem;
    font-weight: bold;
    height: 100%;
    padding: 18px 0;
    width: 100%;
  }
  .v-stepper .disabled {
    opacity: .5;
  }
  /* ステップ2 出題タイトルの設定 */
  .v-stepper .v-stepper__content .quizTitle {
    margin: 0 auto;
    position: relative;
    width: 500px;
  }
  .v-stepper .v-stepper__content .quizTitle .settingBox {
    background: #970812 !important;
    border: 3px solid #ffedd2;
    border-radius: 10px !important;
    color: #fff !important;
    width: 500px;
  }
  .v-stepper .v-stepper__content .quizTitle .settingBox .textItem {
    margin: auto;
    text-align: left;
    width: 90%;
  }
  .v-stepper .v-stepper__content .quizTitle .settingBox .textBox {
    background: #fff;
    border-radius: 10px;
    margin: 10px auto 0;
    width: 90%;
  }
  .v-stepper .v-stepper__content .quizTitle .settingBox .textBox .titleBox {
    outline: none;
    padding: 5px 10px;
    text-align: center;
    width: 100%;
  }
  .v-stepper .v-stepper__content .quizTitle .settingBox .textCount {
    font-size: 0.8rem;
    margin: 3px auto 0;
    text-align: right;
    width: 90%;
  }
</style>