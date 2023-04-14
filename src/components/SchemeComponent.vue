<template>
  <div class="scheme-wrapper">
    <div class="scheme">
      <ContainerComponent>
        <h1 class="scheme-title">СХЕМА СОТРУДНИЧЕСТВА С НАМИ</h1>
        <p class="scheme-description">
          Создает сильную команду единомышленников с единой корпоративной
          культурой. Постоянное развитие и совершенствование, командный дух,
          инновационность, инициативность и проактивность – фундаментальные
          элементы корпоративной культуры компании.
        </p>
      </ContainerComponent>
      <div class="scheme-big-numbers">
        <div class="scheme-big-numbers-one">
          <h1 class="scheme-big-numbers__number">1</h1>
          <p class="scheme-big-numbers__description">
            Принимаем вашу заявку и рассчитываем тариф за 15 минут
          </p>
        </div>
        <div class="scheme-big-numbers-two">
          <h1 class="scheme-big-numbers__number">2</h1>
          <p class="scheme-big-numbers__description">Заключаем договор</p>
        </div>
        <div class="scheme-big-numbers-three">
          <h1 class="scheme-big-numbers__number">3</h1>
          <p class="scheme-big-numbers__description">
            Предоставляем транзитные, экспортно-импортные коды в течение 15
            минут по основным территориям с момента оплаты счета
          </p>
        </div>
        <div class="scheme-big-numbers-four">
          <h1 class="scheme-big-numbers__number">4</h1>
          <p class="scheme-big-numbers__description">
            После отправки вагона Вы отправляете нам отгрузочную накладную
          </p>
        </div>
        <div class="scheme-big-numbers-five">
          <h1 class="scheme-big-numbers__number">5</h1>
          <p class="scheme-big-numbers__description">
            Обмениваемся документами
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ContainerComponent from "@/components/ContainerComponent.vue";

@Component({
  components: {
    ContainerComponent,
  },
})
export default class SchemeComponent extends Vue {}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.scheme {
  background-image: url("@/assets/images/scheme.jpg");
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  padding-top: toVw(30px);
  height: toVw(600px);
  &-title {
    font-size: toVw(32px);
    font-weight: 800;
    color: #1f4287;
    margin-bottom: toVw(55px);
    margin-bottom: toVw(23px);
  }
  &-description {
    font-size: toVw(13px);
    font-weight: 300;
    color: #344552;
  }
  &-big-numbers > div {
    display: flex;
  }
  &-big-numbers {
    display: flex;
    .scheme-big-numbers__number {
      font-size: toVw(44px);
      color: #103f7c;
      margin-right: toVw(17px);
    }
    .scheme-big-numbers__description {
      font-size: toVw(16px);
      color: #344552;
    }
    &-one {
      padding-top: toVw(45px);
      padding-left: toVw(255px);
      .scheme-big-numbers__description {
        max-width: toVw(200px);
      }
    }
    &-two {
      padding-top: toVw(340px);
      padding-left: toVw(80px);
      .scheme-big-numbers__description {
        max-width: toVw(94px);
      }
    }
    &-three {
      padding-top: toVw(30px);
      padding-left: toVw(155px);
      .scheme-big-numbers__description {
        max-width: toVw(308px);
      }
    }
    &-four {
      padding-left: toVw(47.5px);
      padding-top: toVw(300px);
      .scheme-big-numbers__description {
        max-width: toVw(192px);
      }
    }
    &-five {
      .scheme-big-numbers__description {
        max-width: toVw(124px);
      }
    }
  }
}
</style>
