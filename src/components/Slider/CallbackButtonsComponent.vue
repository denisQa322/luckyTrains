<template>
  <div class="callback-buttons__wrapper">
    <div class="outer-circle">
      <div class="inner-circle">
        <button class="callback-btn" @click="showMenu()">
          <img src="../../assets/icons/callback-menu.svg" alt="" />
        </button>
      </div>
    </div>
    <button class="close-callback" @click="closeMenu()">
      <img src="../../assets/icons/close-menu.svg" alt="" />
    </button>
    <div class="callback-buttons__menu">
      <ul class="callback-menu_list">
        <li><button @click="getCall()">Заказать звонок</button></li>
        <li><button @click="textMessage()">Написать сообщение</button></li>
        <li><button @click="countRate()">Рассчитать тариф</button></li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class CallbackButtonsComponent extends Vue {
  showMenu() {
    this.$emit("showMenu");
  }
  closeMenu() {
    this.$emit("closeMenu");
  }
  getCall() {
    this.$emit("getCall");
  }
  textMessage() {
    this.$emit("textMessage");
  }
  countRate() {
    this.$emit("countRate");
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.callback-buttons__wrapper {
  button {
    z-index: 100;
    color: #ffffff;
    font-size: toVw(11px);
    font-weight: 400;
    cursor: pointer;
    border: none;
    background-color: #ff1515;
  }
  .callback-btn {
    border-radius: 50%;
    padding: toVw(9px) toVw(8px) toVw(10px) toVw(11px);
    position: absolute;
    right: toVw(6.5px);
    top: toVw(6px);
    z-index: 1000;
    img {
      width: toVw(23px);
      height: toVw(23px);
    }
  }
  .close-callback {
    position: absolute;
    background: none;
    opacity: 0;
    z-index: 99;
    right: toVw(88px);
    top: toVw(345px);
    transition: 0.6s;
    img {
      width: toVw(25px);
      height: toVw(25px);
    }
  }
  .callback-menu_list {
    z-index: 100;
    opacity: 0;
    justify-content: space-between;
    gap: toVw(8px);
    position: absolute;
    right: toVw(147px);
    top: toVw(340px);
    transition: 0.6s;
    button {
      padding: toVw(11px) toVw(20px);
      border-radius: toVw(33px);
    }
  }
}
.outer-circle {
  border-radius: 50%;
  width: toVw(71px);
  height: toVw(71px);
  background-color: rgba(255, 21, 21, 0.2);
  position: absolute;
  right: toVw(66px);
  top: toVw(320px);
  z-index: 98;
  transition: 0.6s;
}
.inner-circle {
  width: toVw(56px);
  height: toVw(56px);
  border-radius: 50%;
  background-color: rgba(255, 21, 21, 0.7);
  position: absolute;
  right: toVw(7.5px);
  top: toVw(7.5px);
  z-index: 99;
  transition: 0.6s;
}
</style>
