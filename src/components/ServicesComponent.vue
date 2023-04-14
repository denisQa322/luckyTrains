<template>
  <div class="services-wrapper">
    <ContainerComponent :styleType="containerType.FLEX_BETWEEN">
      <div class="services-info">
        <h1 class="services-header">НАШИ УСЛУГИ</h1>
        <h4 class="services-red-header">Работаем для вас с 2014 года</h4>
        <p class="services-text">
          За 17 лет работы с нашими клиентами и партнерами мы готовы взять на
          себя расчет и <br />
          оплату тарифов, а также остальных возможных сборов за ваши вагоны.
          Сэкономим ваше бесценное время! <br />
          Создает сильную команду единомышленников с единой корпоративной
          культурой. <br />
          Постоянное развитие и совершенствование, командный дух,
          инновационность,
          <br />
          инициативность и проактивность – фундаментальные элементы
          корпоративной культуры <br />
          компании.
        </p>
      </div>
      <div class="services-image-wrapper">
        <div class="service-red-bg"></div>
        <div class="service-image-bg">
          <img src="@/assets/icons/train.svg" alt="" />
          <p>
            Оплата железнодорожного <br />
            тарифа по территориям
          </p>
          <div class="service-get-call">
            <button class="btn-order" @click="openOrder()">
              Заказать услугу
              <img src="@/assets/icons/right-arrow.svg" alt="" />
            </button>
          </div>
        </div>
      </div>
    </ContainerComponent>
    <OrderServiceComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/ContainerComponent.vue";
import { ContainerType } from "@/components/ContainerComponent.vue";
import OrderServiceComponent from "@/components/Modals/OrderServiceComponent.vue";

@Component({
  components: {
    ContainerComponent,
    OrderServiceComponent,
  },
})
export default class ServicesComponent extends Vue {
  containerType = ContainerType;
  openOrder() {
    const sendOrder: HTMLElement = document.querySelector(
      ".order-service-wrapper"
    ) as HTMLElement;

    sendOrder.style.visibility = "visible";
    sendOrder.style.opacity = "1";
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";

h1 {
  font-size: toVw(32px);
  font-weight: 800;
  color: #1f4287;
  margin-bottom: toVw(30px);
}
h4 {
  font-size: toVw(25px);
  font-weight: 800;
  margin-bottom: toVw(35px);
  color: #ff1515;
}
p {
  font-size: toVw(16px);
  font-weight: 400;
  color: #344552;
}

.services-image-wrapper {
  height: toVw(350px);
  .service-red-bg {
    width: toVw(420px);
    height: toVw(304px);
    position: relative;
    background-color: #ff1515;
    z-index: 9;
    top: toVw(29px);
    right: toVw(-27px);
    border-radius: toVw(17px) toVw(23px);
  }
  .service-image-bg {
    width: toVw(437px);
    height: toVw(320px);
    border-radius: toVw(23px) toVw(15px);
    background-image: url("@/assets/images/services-image.jpg");
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    text-align: center;
    position: relative;
    top: toVw(-300px);
    z-index: 10;
    padding-top: toVw(85px);
    img {
      width: toVw(70px);
      height: toVw(53px);
      margin-bottom: toVw(39px);
    }
    p {
      color: #ffffff;
      padding: 0;
      margin-bottom: toVw(30px);
    }
    .service-get-call {
      button {
        background: none;
        border: none;
        cursor: pointer;
        font-size: toVw(20px);
        color: #ffffff;
        font-weight: 500;
        margin-right: toVw(12px);
        img {
          cursor: pointer;
          margin: 0;
          width: toVw(8px);
          height: toVw(7px);
        }
      }
    }
  }
}
</style>
