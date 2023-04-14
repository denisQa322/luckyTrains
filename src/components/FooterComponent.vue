<template>
  <div class="footer-wrapper">
    <div class="footer-top">
      <ContainerComponent :styleType="containerType.FLEX_BETWEEN">
        <div class="footer-top-logo">
          <router-link to="/">
            <img src="../assets/images/logo.jpg" alt="" />
          </router-link>
        </div>
        <MenuComponent />
        <div class="footer-top-socials">
          <a href="https://whatsapp.com"
            ><img src="../assets/icons/whatsapp.svg" alt=""
          /></a>
          <a href="https://skype.com"
            ><img src="../assets/icons/skype.svg" alt=""
          /></a>
        </div>
        <div class="footer-top-feedback">
          <div class="footer-top-feedback-call">
            <a href="tel:8 800 808-80-00">
              <img src="../assets/icons/red-phone.svg" alt="" />
            </a>
            <a href="tel:8 800 808-80-00">8 800 808-80-00</a>
          </div>
          <div class="footer-top-feedback-mail">
            <a href="mailto:info@trans.kz">
              <img src="../assets/icons/red-mail.svg" alt="" />
            </a>
            <a href="mailto:info@trans.kz">info@trans.kz</a>
          </div>
        </div>
      </ContainerComponent>
    </div>
    <div class="footer-bottom">
      <ContainerComponent>
        <div class="footer-bottom-rights">Все права защищены. © 2006-2020</div>
        <div class="footer-bottom-created">
          Разработал <a href="https://t.me/denisQa322">Денис Исаков</a>
        </div>
      </ContainerComponent>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/ContainerComponent.vue";
import { ContainerType } from "@/components/ContainerComponent.vue";
import MenuComponent from "@/components/MenuComponent.vue";

@Component({
  components: {
    ContainerComponent,
    MenuComponent,
  },
})
export default class FooterComponent extends Vue {
  containerType = ContainerType;
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.container {
  align-items: center;
}
.container.flex-between {
  padding-top: toVw(30px);
  padding-bottom: toVw(30px);
  border-bottom: toVw(0.6px) solid #dbdbdb;
}
.footer-top {
  &-logo {
    img {
      width: toVw(196px);
      height: toVw(81px);
    }
  }
  &-socials {
    display: flex;
    gap: toVw(20px);
    a {
      img {
        width: toVw(22px);
        height: toVw(22px);
      }
    }
  }
  &-feedback {
    &-call {
      margin-bottom: toVw(10px);
      margin-right: toVw(30px);
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
      margin-right: toVw(30px);
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
.footer-bottom {
  padding-top: toVw(32px);
  padding-bottom: toVw(45px);
  .container {
    display: flex;
    justify-content: space-between;
    .footer-bottom-rights {
      font-size: toVw(13px);
      font-weight: 400;
      color: #103f7c;
    }
    .footer-bottom-created {
      font-size: toVw(13px);
      font-weight: 400;
      color: #103f7c;
      a {
        font-size: toVw(13px);
        font-weight: 400;
        color: #103f7c;
      }
    }
  }
}
</style>
