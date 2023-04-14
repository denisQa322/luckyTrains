<template>
  <div class="get-call-wrapper">
    <div class="get-call">
      <form onsubmit="return false">
        <h1 class="get-call-header">ЗАКАЗАТЬ ЗВОНОК</h1>
        <p class="get-call-description">
          И мы свяжемся с вами в течении 15 минут
        </p>
        <input
          class="get-call-name"
          type="text"
          placeholder="Ваше имя"
          v-model="YourName"
          required
        />
        <input
          class="get-call-phone"
          type="tel"
          maxlength="12"
          placeholder="+7 (___) ___-__-__"
          v-model="YourPhone"
          required
        />
        <button class="get-call-send" @click="callSend()">ОТПРАВИТЬ</button>
      </form>
      <button class="get-call-close" @click="closeCall()">&#10006;</button>
    </div>
    <CallSendComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import CallSendComponent from "@/components/Modals/CallSendComponent.vue";

@Component({
  components: {
    CallSendComponent,
  },
})
export default class GetCallComponent extends Vue {
  YourName = "";
  YourPhone = "";
  closeCall() {
    const closeModalCall: HTMLElement = document.querySelector(
      ".get-call-wrapper"
    ) as HTMLElement;
    const bodyModalCall: HTMLElement = document.querySelector(
      "body"
    ) as HTMLElement;

    closeModalCall.style.opacity = "0";
    closeModalCall.style.visibility = "hidden";
    bodyModalCall.addEventListener("click", (event) => {
      if (event.target === closeModalCall) {
        closeModalCall.style.opacity = "0";
        closeModalCall.style.visibility = "hidden";
      }
    });
  }
  callSend() {
    const callSendThanks: HTMLElement = document.querySelector(
      ".modal-send-call-wrapper"
    ) as HTMLElement;
    if ((this.YourName === "", this.YourPhone === "")) {
      return;
    } else {
      callSendThanks.style.opacity = "1";
      callSendThanks.style.visibility = "visible";
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.get-call-wrapper {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  transition: 0.5s;
  opacity: 0;
  visibility: hidden;
  z-index: 1000;
}
.get-call {
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
    .get-call-header {
      color: #172675;
      font-size: toVw(32px);
      font-weight: 800;
      margin-bottom: toVw(17px);
    }
    .get-call-description {
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
    .get-call-send {
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
  .get-call-close {
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
