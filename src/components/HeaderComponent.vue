<template>
  <header class="header">
    <ContainerComponent :styleType="containerType.FLEX_BETWEEN">
      <div class="header-logo">
        <router-link to="/">
          <img src="../assets/images/logo.jpg" alt="" />
        </router-link>
      </div>
      <MenuComponent />
      <button class="request-btn" @click="sendRequest()">
        Запрос на перевозку
      </button>
      <div class="feedback">
        <div class="feedback-call">
          <a href="tel:8 800 808-80-00">
            <img src="../assets/icons/red-phone.svg" alt="" />
          </a>
          <a href="tel:8 800 808-80-00">8 800 808-80-00</a>
        </div>
        <div class="feedback-mail">
          <a href="mailto:info@trans.kz">
            <img src="../assets/icons/red-mail.svg" alt="" />
          </a>
          <a href="mailto:info@trans.kz">info@trans.kz</a>
        </div>
      </div>
    </ContainerComponent>
    <RequestTransportationComponent />
    <div class="burger-wrapper">
      <div class="burger" @click="openMenu()">
        <span class="burger-line"></span>
        <span class="burger-line"></span>
        <span class="burger-line"></span>
      </div>
      <button class="burger-close" @click="closeMenu()">&#10006;</button>
    </div>
  </header>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/ContainerComponent.vue";
import { ContainerType } from "@/components/ContainerComponent.vue";
import MenuComponent from "@/components/MenuComponent.vue";
import RequestTransportationComponent from "@/components/Modals/RequestTransportationComponent.vue";

@Component({
  components: {
    ContainerComponent,
    MenuComponent,
    RequestTransportationComponent,
  },
})
export default class HeaderComponent extends Vue {
  containerType = ContainerType;
  sendRequest() {
    const sendRequest: HTMLElement = document.querySelector(
      ".request-call-wrapper"
    ) as HTMLElement;

    sendRequest.style.visibility = "visible";
    sendRequest.style.opacity = "1";
  }
  openMenu() {
    const menu: HTMLElement = document.querySelector(".menu") as HTMLElement;
    const menuList: HTMLElement = document.querySelector(
      ".menu_list"
    ) as HTMLElement;
    const burgerCloseELement: HTMLElement = document.querySelector(
      ".burger-close"
    ) as HTMLElement;
    const burgerElement: HTMLElement = document.querySelector(
      ".burger"
    ) as HTMLElement;

    burgerElement.style.display = "none";
    burgerCloseELement.style.display = "block";
    menu.style.display = "block";
    menuList.style.display = "block";
    menuList.style.flexDirection = "column";
    menuList.style.height = "100vh";
    menuList.style.fontSize = "30px";
    menuList.style.position = "absolute";
    menuList.style.backgroundColor = "rgba(0,0,0,0.9)";
    menuList.style.inset = "0";
    menuList.style.zIndex = "1000";
    menuList.style.color = "white";
    menuList.style.right = "0";
    burgerCloseELement.style.zIndex = "1010";
  }

  closeMenu() {
    const burgerCloseELement: HTMLElement = document.querySelector(
      ".burger-close"
    ) as HTMLElement;
    const menuList: HTMLElement = document.querySelector(
      ".menu"
    ) as HTMLElement;
    const burgerElement: HTMLElement = document.querySelector(
      ".burger"
    ) as HTMLElement;
    burgerCloseELement.style.display = "none";
    menuList.style.display = "none";
    burgerElement.style.display = "block";
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.container {
  align-items: center;
}
.header {
  position: relative;
  padding-top: toVw(20px);
  padding-bottom: toVw(40px);
  .burger-close {
    display: none;
  }
  &-logo {
    img {
      width: toVw(183px);
      height: toVw(76px);
    }
  }
  .request-btn {
    padding: toVw(14px) toVw(20px);
    background-color: #ff1515;
    font-size: toVw(14px);
    display: flex;
    font-weight: 400;
    color: #ffffff;
    border: none;
    border-radius: toVw(5px);
    cursor: pointer;
  }
  .feedback {
    display: flex;
    gap: toVw(30px);
    flex-direction: column;
    &-call {
      img {
        margin-right: toVw(15px);
        width: toVw(20px);
        height: toVw(20px);
      }
      a {
        font-size: toVw(21px);
      }
    }
    &-mail {
      img {
        margin-right: toVw(15px);
        width: toVw(17px);
        height: toVw(12px);
      }
      a {
        font-size: toVw(21px);
      }
    }
  }
}
</style>
