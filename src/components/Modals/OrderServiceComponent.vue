<template>
  <div class="order-service-wrapper">
    <div class="order-service">
      <form onsubmit="return false">
        <h1 class="order-service-header">ЗАКАЗАТЬ ЗВОНОК</h1>
        <p class="order-service-description">
          И мы свяжемся с вами в течении 15 минут
        </p>
        <input
          class="order-service-name"
          type="text"
          placeholder="Ваше имя"
          v-model="YourName"
          required
        />
        <input
          class="order-service-phone"
          type="tel"
          maxlength="12"
          placeholder="+7 (___) ___-__-__"
          v-model="YourPhone"
          required
        />
        <button class="order-service-send" @click="callOrder()">
          ОТПРАВИТЬ
        </button>
      </form>
      <button class="order-service-close" @click="closeOrder()">
        &#10006;
      </button>
    </div>
    <ThanksOrderSendComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ThanksOrderSendComponent from "@/components/Modals/ThanksOrderSendComponent.vue";

@Component({
  components: { ThanksOrderSendComponent },
})
export default class OrderServiceComponent extends Vue {
  YourName = "";
  YourPhone = "";
  closeOrder() {
    const closeModalOrder: HTMLElement = document.querySelector(
      ".order-service-wrapper"
    ) as HTMLElement;
    const bodyModalOrder: HTMLElement = document.querySelector(
      "body"
    ) as HTMLElement;

    closeModalOrder.style.opacity = "0";
    closeModalOrder.style.visibility = "hidden";
    bodyModalOrder.addEventListener("click", (event) => {
      if (event.target === closeModalOrder) {
        closeModalOrder.style.opacity = "0";
        closeModalOrder.style.visibility = "hidden";
      }
    });
  }
  callOrder() {
    const callSendOrder: HTMLElement = document.querySelector(
      ".modal-order-wrapper"
    ) as HTMLElement;
    if ((this.YourName === "", this.YourPhone === "")) {
      return;
    } else {
      callSendOrder.style.opacity = "1";
      callSendOrder.style.visibility = "visible";
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.order-service-wrapper {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: 0.5s;
  opacity: 0;
  visibility: hidden;
  z-index: 1000;
}
.order-service {
  width: toVw(774px);
  position: relative;
  background-color: #ffffff;
  margin: auto;
  border-radius: toVw(22px);
  padding: toVw(84px) toVw(97px);
  form {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-direction: column;
    .order-service-header {
      color: #172675;
      font-size: toVw(32px);
      font-weight: 800;
      margin-bottom: toVw(17px);
    }
    .order-service-description {
      margin-bottom: toVw(26px);
      font-size: toVw(14px);
      font-weight: 500;
      color: #535353;
    }
    input {
      padding: toVw(25px);
      width: toVw(580px);
      font-size: toVw(14px);
      font-weight: 500;
      color: #535353;
      margin-bottom: toVw(15px);
      border-radius: toVw(8px);
      border: toVw(1px) solid #8e8e8e;
    }
    input::placeholder {
      color: #535353;
    }
    .order-service-send {
      font-size: toVw(15px);
      font-weight: 500;
      background-color: #ff1515;
      padding: toVw(16px) toVw(32px);
      border-radius: toVw(7px);
      border: none;
      color: #ffffff;
      cursor: pointer;
    }
  }
  .order-service-close {
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
