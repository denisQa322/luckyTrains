<template>
  <div class="benefits">
    <ContainerComponent :styleType="containerType.GRID">
      <div
        class="benefits-item"
        v-for="(benefit, index) in benefits"
        :key="index"
        :benefit="benefit"
      >
        <div class="benefits-img"><img :src="benefit.image" alt="" /></div>
        <div class="benefits-info">
          <div class="benefits-info__header">{{ benefit.title }}</div>
          <div class="benefits-info__description">
            {{ benefit.description }}
          </div>
        </div>
      </div>
    </ContainerComponent>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { IBenefitItem } from "@/types/benefitItem";
import ContainerComponent from "@/components/ContainerComponent.vue";
import { ContainerType } from "@/components/ContainerComponent.vue";

@Component({
  components: {
    ContainerComponent,
  },
  props: {
    benefit: {
      type: Object as () => IBenefitItem,
    },
  },
})
export default class BenefitsComponent extends Vue {
  containerType = ContainerType;
  benefits: IBenefitItem[] = [
    {
      image: require("@/assets/icons/insurance.svg"),
      title: "Страхование груза",
      description:
        "Создает сильную команду единомышленников с единой корпоративной культурой. Постоянное развитие и совершенствование, командный дух, инновационность, инициативность и проактивность – фундаментальные элементы корпоративной культуры компании.",
    },
    {
      image: require("@/assets/icons/logistics.svg"),
      title: "Высокий класс логистических услуг",
      description:
        "Создает сильную команду единомышленников с единой корпоративной культурой. Постоянное развитие и совершенствование, командный дух, инновационность, инициативность и проактивность – фундаментальные элементы корпоративной культуры компании.",
    },
    {
      image: require("@/assets/icons/calculator.svg"),
      title: "Доступные цены ",
      description:
        "Создает сильную команду единомышленников с единой корпоративной культурой. Постоянное развитие и совершенствование, командный дух, инновационность, инициативность и проактивность – фундаментальные элементы корпоративной культуры компании.",
    },
    {
      image: require("@/assets/icons/person.svg"),
      title: "Индивидуальный подход",
      description:
        "Создает сильную команду единомышленников с единой корпоративной культурой. Постоянное развитие и совершенствование, командный дух, инновационность, инициативность и проактивность – фундаментальные элементы корпоративной культуры компании.",
    },
  ];
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.benefits {
  border-bottom: toVw(0.6px) solid #dbdbdb;
  .benefits-item {
    display: flex;
    justify-content: space-between;
    height: toVw(100px);
    margin-bottom: toVw(56px);
    .benefits-img {
      background-color: #ff1515;
      border-radius: toVw(7px);
      height: toVw(100px);
      width: toVw(92px);
      padding: toVw(25px) toVw(20px);
      margin-right: toVw(27px);
      img {
        width: toVw(50px);
        height: toVw(44px);
      }
    }
    .benefits-info {
      color: #344552;
      &__header {
        font-size: toVw(18px);
        font-weight: 600;
        margin-bottom: toVw(13px);
      }
      &__description {
        font-size: toVw(13px);
        font-weight: 300;
      }
    }
  }
}
.benefits {
  border-bottom: toVw(0.6px) solid #dbdbdb;
  padding-bottom: toVw(75px);
}
</style>
