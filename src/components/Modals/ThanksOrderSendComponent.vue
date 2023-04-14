<template>
  <div class="modal-order-wrapper">
    <div class="modal-order">
      <h1 class="modal-order-header">Спасибо</h1>
      <p class="modal-order-description">
        Запрос уже улетел для оперативного просчета ставки. Детальная обработка
        запроса занимает время, поэтому если решение вопроса требовалось *еще
        вчера* - свяжитесь с экспертами в ближайшем офисе AsstrA. А пока
        присоединяйтесь к AsstrA в социальных сетях!
      </p>
      <div class="modal-order-images">
        <a href="https://whatsapp.com"
          ><img src="../../assets/icons/whatsapp.svg" alt=""
        /></a>
        <a href="https://skype.com"
          ><img src="../../assets/icons/skype.svg" alt=""
        /></a>
      </div>
      <p class="modal-order-text">
        Переходите по ссылкам, жмите кнопку «Нравится» и будьте в курсе новостей
        мира логистики.
      </p>
      <button class="modal-order-close" @click="closeThanks()">&#10006;</button>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class ThanksOrderSendComponent extends Vue {
  closeThanks() {
    const modalThanks: HTMLElement = document.querySelector(
      ".modal-order-wrapper"
    ) as HTMLElement;
    const bodyElement: HTMLElement = document.querySelector(
      "body"
    ) as HTMLElement;

    modalThanks.style.opacity = "0";
    modalThanks.style.visibility = "hidden";
    bodyElement.addEventListener("click", (event) => {
      if (event.target === modalThanks) {
        modalThanks.style.opacity = "0";
        modalThanks.style.visibility = "hidden";
      }
    });
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.modal-order-wrapper {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  visibility: hidden;
  opacity: 0;
  transition: 0.5s;
  z-index: 1000;
}
.modal-order {
  max-width: toVw(1025px);
  position: relative;
  background-color: #ffffff;
  margin: auto;
  border-radius: toVw(22px);
  padding: toVw(91px) toVw(123px) toVw(93px) toVw(77px);
  &-header {
    font-size: toVw(55px);
    font-weight: 500;
    color: #ff1515;
    margin-bottom: toVw(33px);
    line-height: toVw(71px);
  }

  &-description {
    font-size: toVw(16px);
    font-weight: 400;
    margin-bottom: toVw(25px);
    color: #344552;
    line-height: toVw(21px);
  }
  &-images {
    margin-bottom: toVw(26px);
    display: flex;
    gap: toVw(20px);
    a {
      img {
        width: toVw(22px);
        height: toVw(22px);
      }
    }
  }
  &-text {
    font-size: toVw(16px);
    font-weight: 400;
    color: #344552;
    line-height: toVw(21px);
  }
  &-order {
    position: absolute;
    top: toVw(42px);
    right: toVw(34px);
    color: red;
    font-size: toVw(25px);
    z-index: 100;
    cursor: pointer;
    border: none;
    background: none;
  }
  &-close {
    position: absolute;
    top: toVw(42px);
    right: toVw(34px);
    color: red;
    font-size: toVw(25px);
    z-index: 100;
    cursor: pointer;
    border: none;
    background: none;
  }
}
</style>
