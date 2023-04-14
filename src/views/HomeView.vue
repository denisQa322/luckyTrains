<template>
  <div class="home">
    <section class="first-screen">
      <SliderComponent>
        <div
          v-for="(item, index) in items"
          :key="index"
          :style="{
            backgroundImage: 'url(' + item.bgImage + ')',
          }"
          class="slider-items"
        >
          <div class="slider-item">
            <div class="slider-title">
              {{ item.title }}
            </div>
          </div>
        </div>
      </SliderComponent>
      <ContainerComponent>
        <div class="pay-fast">
          <h1 class="pay-fast__header">
            НЕОБХОДИМО БЫСТРО ОПЛАТИТЬ ЖЕЛЕЗНОДОРОЖНЫЙ ТАРИФ?
          </h1>
          <h4 class="pay-fast__description">
            Без переплаты за покупку валюты и обеспечить беспрепятственный
            проезд подвижного состава?
          </h4>
          <p class="pay-fast__text">
            За 17 лет работы с нашими клиентами и партнерами мы готовы взять на
            себя расчет и оплату тарифов, а <br />
            также остальных возможных сборов за ваши вагоны. Сэкономим ваше
            бесценное время!
          </p>
        </div>
      </ContainerComponent>
    </section>
    <section class="service-section">
      <ContainerComponent>
        <ServicesComponent />
      </ContainerComponent>
    </section>
    <section class="benefits-section">
      <ContainerComponent>
        <div class="benefits-title">
          <h1>ПРЕИМУЩЕСТВА РАБОТЫ С НАМИ</h1>
        </div>
        <BenefitsComponent />
      </ContainerComponent>
    </section>
    <section class="scheme-section">
      <SchemeComponent />
    </section>
    <section class="count-section">
      <CountComponent></CountComponent>
    </section>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import SliderComponent from "@/components/Slider/SliderComponent.vue";
import ContainerComponent from "@/components/ContainerComponent.vue";
import ServicesComponent from "@/components/ServicesComponent.vue";
import { ContainerType } from "@/components/ContainerComponent.vue";
import BenefitsComponent from "@/components/BenefitsComponent.vue";
import SchemeComponent from "@/components/SchemeComponent.vue";
import CountComponent from "@/components/CountComponent.vue";

@Component({
  components: {
    SliderComponent,
    ContainerComponent,
    ServicesComponent,
    BenefitsComponent,
    SchemeComponent,
    CountComponent,
  },
})
export default class HomeView extends Vue {
  containerType = ContainerType;
  items = [
    {
      bgImage: require("../assets/images/slider-colored-trains.jpg"),
      title: "Сопровождаем железнодорожные грузоперевозки",
    },
    {
      bgImage: require("../assets/images/slider-blue-trains.jpg"),
      title: "Услуги по оплате Железнодорожных тарифов",
    },
    {
      bgImage: require("../assets/images/slider-tranfser.jpg"),
      title: "Оплата ж/д тарифов",
    },
    {
      bgImage: require("../assets/images/slider-trains.jpg"),
      title: "Транспортно-экспедиционные услуги",
    },
  ];
  openThanks() {
    const modalText: HTMLElement = document.querySelector(
      ".modal-send-wrapper"
    ) as HTMLElement;
    modalText.style.visibility = "visible";
    modalText.style.opacity = "1";
  }
}
</script>

<style scoped lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Exo:wght@100;200;300;400;500;600;700;800;900&display=swap");
@import "@/assets/scss/toVw.scss";
.first-screen {
  .slider {
    height: toVw(586px);
    width: 100%;
    margin-bottom: toVw(55px);
    .slider-items {
      background-size: cover;
      background-repeat: no-repeat;
      background-position: center;
      .slider-item {
        min-height: toVw(587px);
        min-width: toVw(1920px);
        position: relative;
        .slider-title {
          font-family: sans-serif, "Exo";
          position: absolute;
          top: toVw(232px);
          left: toVw(277px);
          width: toVw(800px);
          font-size: toVw(46px);
          font-weight: 800;
          color: #ffffff;
        }
      }
    }
  }
  .pay-fast {
    border-bottom: toVw(0.6px) solid #dbdbdb;
    padding-bottom: toVw(55px);
    margin-bottom: toVw(75px);
    &__header {
      color: #1f4287;
      font-size: toVw(32px);
      font-weight: 800;
      margin-bottom: toVw(35px);
    }
    &__description {
      font-size: toVw(20px);
      font-weight: 500;
      margin-bottom: toVw(30px);
    }
    &__text {
      font-size: toVw(16px);
      font-weight: 400;
      color: #344552;
    }
  }
}
.service-section {
  margin-bottom: toVw(39px);
}
.benefits-section {
  background-color: #f5f8fb99;
  margin-bottom: toVw(10px);
  .benefits-title {
    h1 {
      font-size: toVw(32px);
      font-weight: 800;
      color: #1f4287;
      margin-bottom: toVw(55px);
    }
  }
}
</style>
