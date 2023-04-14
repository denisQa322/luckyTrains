<template>
  <div class="modal-wrapper">
    <div class="modal-message">
      <form onsubmit="return false">
        <h1 class="modal-message-header">Написать сообщение</h1>
        <p class="modal-message-description">
          И мы свяжемся с вами в течении 15 минут
        </p>
        <input
          class="modal-message-name"
          type="text"
          placeholder="Ваше имя"
          v-model="YourName"
          required
        />
        <input
          class="modal-message-phone"
          type="tel"
          placeholder="+7 (___) ___-__-__"
          maxlength="12"
          v-model="YourPassword"
          required
        />
        <input
          class="modal-message-email"
          type="email"
          placeholder="E-mail"
          v-model="YourMail"
          required
        />
        <textarea
          class="modal-message-message"
          placeholder="Ваш комментарий"
          v-model="YourMessage"
          required
        />
        <button class="modal-message-btn-send" @click="modalThanks()">
          Отправить
        </button>
      </form>
      <button class="modal-message-close" @click="closeText()">&#10006;</button>
    </div>
    <ThanksComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ThanksComponent from "@/components/Modals/ThanksComponent.vue";

@Component({
  components: {
    ThanksComponent,
  },
})
export default class TextMessageComponent extends Vue {
  YourName = "";
  YourPassword = "";
  YourMessage = "";
  YourMail = "";
  closeText() {
    const closeModalText: HTMLElement = document.querySelector(
      ".modal-wrapper"
    ) as HTMLElement;
    const bodyModalText: HTMLElement = document.querySelector(
      "body"
    ) as HTMLElement;

    closeModalText.style.opacity = "0";
    closeModalText.style.visibility = "hidden";
    bodyModalText.addEventListener("click", (event) => {
      if (event.target === closeModalText) {
        closeModalText.style.opacity = "0";
        closeModalText.style.visibility = "hidden";
      }
    });
  }
  modalThanks() {
    const thanksButton: HTMLElement = document.querySelector(
      ".modal-send-wrapper"
    ) as HTMLElement;
    if (
      (this.YourName === "",
      this.YourPassword === "",
      this.YourMessage === "",
      this.YourMail === "")
    ) {
      return;
    } else {
      console.log("thanksButton", thanksButton);
      thanksButton.style.visibility = "visible";
      thanksButton.style.opacity = "1";
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.modal-wrapper {
  position: fixed;
  inset: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  visibility: hidden;
  opacity: 0;
  z-index: 1000;
  transition: 0.5s;
}
.modal-message {
  max-width: toVw(1025px);
  position: relative;
  background-color: #ffffff;
  margin: auto;
  border-radius: toVw(22px);
  padding: toVw(91px) toVw(123px) toVw(93px) toVw(77px);

  form {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
    flex-direction: column;

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
    .modal-message-header {
      margin-bottom: toVw(17px);
      font-size: toVw(32px);
      font-weight: 800;
      color: #172675;
    }
    .modal-message-description {
      margin-bottom: toVw(26px);
      font-size: toVw(14px);
      font-weight: 500;
      color: #535353;
    }
    .modal-message-message {
      height: toVw(160px);
      width: toVw(580px);
      padding: toVw(25px);
      margin-bottom: toVw(15px);
      font-size: toVw(14px);
      font-weight: 500;
      color: #535353;
      &::placeholder {
        color: #535353;
      }
    }
    .modal-message-btn-send {
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
}
.modal-message-close {
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
</style>
