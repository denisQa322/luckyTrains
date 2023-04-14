<template>
  <div class="count">
    <form onsubmit="return false">
      <h1 class="count-header">ОСТАВЬТЕ ЗАЯВКУ</h1>
      <div class="count-inputs">
        <input
          class="count-name"
          type="text"
          placeholder="Ваше имя"
          v-model="YourName"
          required
        />
        <input
          class="count-tel"
          type="tel"
          maxlength="12"
          placeholder="+7 (___) ___-__-__"
          v-model="YourPhone"
          required
        />
      </div>
      <button class="btn-send" @click="openSend()">ПРОКОНСУЛТИРОВАТЬСЯ</button>
    </form>
    <SendComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import SendComponent from "@/components/Modals/SendComponent.vue";

@Component({
  components: {
    SendComponent,
  },
})
export default class CountComponent extends Vue {
  YourName = "";
  YourPhone = "";
  //*openThanks
  openSend() {
    const modalSend: HTMLElement = document.querySelector(
      ".modal-send-message-wrapper"
    ) as HTMLElement;
    if ((this.YourName === "", this.YourPhone === "")) {
      return;
    } else {
      modalSend.style.visibility = "visible";
      modalSend.style.opacity = "1";
    }
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.count {
  height: toVw(472px);
  background-image: url("@/assets/images/count-bg.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  form {
    margin-left: toVw(946px);
    padding-top: toVw(110px);
    .count-header {
      color: #ffffff;
      font-size: toVw(38px);
      font-weight: 800;
      margin-bottom: toVw(38px);
    }
    .count-inputs {
      background-color: none;
      display: flex;
      flex-direction: column;
      margin-bottom: tovw(40px);
      input {
        color: #ffffff;
        border-radius: toVw(8px);
        border: toVw(1px) solid #ffffff;
        background: transparent;
        padding: toVw(21px) toVw(24px);
        width: toVw(580px);
        margin-bottom: toVw(15px);
        ::placeholder {
          color: #ffffff;
        }
      }
    }
    button {
      cursor: pointer;
      font-size: toVw(15px);
      color: #ffffff;
      background-color: #ff1515;
      border: none;
      border-radius: toVw(7px);
      padding: toVw(16px) toVw(30px);
      width: toVw(268px);
    }
  }
}
</style>
