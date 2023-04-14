<template>
  <div class="slider">
    <div class="buttons">
      <div class="slider-buttons">
        <SliderButtonsComponent
          :showControls="true"
          @arrowLeftClickHandler="clickOnLeft()"
          @arrowRightClickHandler="clickOnRight()"
          :disabledRight="this.offset >= this.maxSliderLineWidth"
          :disabledLeft="!this.offset"
        />
      </div>
      <div class="callback-buttons">
        <CallbackButtonsComponent
          @showMenu="openMenu()"
          @closeMenu="coverMenu()"
          @getCall="callBack()"
          @textMessage="getMessage()"
          @countRate="calculateRate()"
        />
      </div>
      <div class="exchange-rate">
        <ul class="exchange-rate-menu">
          <li class="dollar"><a href="https://kurs.kz/">EUR 493</a></li>
          |
          <li class="euro"><a href="https://kurs.kz/">USD 451</a></li>
          |
          <li class="rubles"><a href="https://kurs.kz/">RUB 5.6</a></li>
        </ul>
      </div>
    </div>
    <div class="slider-items-line" ref="sliderItems">
      <template>
        <slot> </slot>
      </template>
    </div>
    <GetCallComponent />
    <TextMessageComponent />
    <CalculateRateComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import SliderItemComponent from "./SliderItemComponent.vue";
import { ISliderItem } from "@/types/sliderItem";
import SliderButtonsComponent from "./SliderButtonsComponent.vue";
import CallbackButtonsComponent from "./CallbackButtonsComponent.vue";
import TextMessageComponent from "@/components/Modals/TextMessageComponent.vue";
import GetCallComponent from "../Modals/GetCallComponent.vue";
import CalculateRateComponent from "../Modals/CalculateRateComponent.vue";

@Component({
  components: {
    SliderItemComponent,
    SliderButtonsComponent,
    CallbackButtonsComponent,
    TextMessageComponent,
    GetCallComponent,
    CalculateRateComponent,
  },
  props: {
    items: {
      type: Array as () => ISliderItem[],
      required: false,
      default: () => [],
    },
    itemsInSlider: {
      type: Number,
      required: false,
      default: 1,
    },
  },
})
export default class SliderComponent extends Vue {
  //*Slider
  offset = 0;
  sliderItemWidth = 0;
  gapCssProp = 0;
  maxSliderLineWidth = 0;
  mounted() {
    const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;

    this.sliderItemWidth = listElement.children[0].clientWidth;

    this.maxSliderLineWidth =
      this.sliderItemWidth *
        (listElement.children.length - (this.$props.itemsInSlider - 1)) -
      this.sliderItemWidth;

    const gapCssProp = window
      .getComputedStyle(listElement, null)
      .getPropertyValue("gap");

    this.gapCssProp = parseInt(gapCssProp);
  }

  clickOnRight() {
    if (this.offset >= this.maxSliderLineWidth) {
      return;
    }

    const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
    this.offset = this.offset + (this.gapCssProp + this.sliderItemWidth);
    listElement.style.transform = `translateX(${-this.offset}px)`;
  }

  clickOnLeft() {
    if (!this.offset) {
      return;
    }
    const listElement: HTMLElement = this.$refs.sliderItems as HTMLElement;
    this.offset = this.offset - (this.gapCssProp + this.sliderItemWidth);
    listElement.style.transform = `translateX(${-this.offset}px)`;
  }
  //*Open Menu
  openMenu() {
    const openMenuButton: HTMLElement = document.querySelector(
      ".outer-circle"
    ) as HTMLElement;
    const closeButton = document.querySelector(
      ".close-callback"
    ) as HTMLElement;
    const callbackButtonsMenu = document.querySelector(
      ".callback-menu_list"
    ) as HTMLElement;

    callbackButtonsMenu.style.visibility = "visible";
    callbackButtonsMenu.style.display = "flex";
    callbackButtonsMenu.style.opacity = "1";
    openMenuButton.style.top = "13.0208333333vw";
    closeButton.style.visibility = "visible";
    closeButton.style.opacity = "1";
  }
  //*Close Menu
  coverMenu() {
    const coverMenuButton = document.querySelector(
      ".outer-circle"
    ) as HTMLElement;
    const closeButton = document.querySelector(
      ".close-callback"
    ) as HTMLElement;
    const callbackButtonsMenu = document.querySelector(
      ".callback-menu_list"
    ) as HTMLElement;

    callbackButtonsMenu.style.visibility = "hidden";
    callbackButtonsMenu.style.opacity = "0";
    closeButton.style.visibility = "hidden";
    closeButton.style.opacity = "0";
    coverMenuButton.style.top = "16.6666666667vw";
  }
  //*Get Call
  callBack() {
    const modalCall = document.querySelector(
      ".get-call-wrapper"
    ) as HTMLElement;
    modalCall.style.visibility = "visible";
    modalCall.style.opacity = "1";
  }
  //*Text Message
  getMessage() {
    const modalText = document.querySelector(".modal-wrapper") as HTMLElement;
    modalText.style.visibility = "visible";
    modalText.style.opacity = "1";
  }
  //*Count Rate
  calculateRate() {
    const countRate = document.querySelector(
      ".modal-rate-wrapper"
    ) as HTMLElement;
    countRate.style.visibility = "visible";
    countRate.style.opacity = "1";
  }
}
</script>
<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.slider {
  position: relative;
  overflow: hidden;
  min-width: 100%;
  height: toVw(586px);
  .buttons {
    display: flex;
  }
  .slider-items-line {
    display: flex;
    flex-direction: row;
    transition: 0.5s;
    gap: toVw(30px);
  }
}
.exchange-rate {
  position: relative;
  top: toVw(100px);
  left: toVw(1316px);
  z-index: 100;
  .exchange-rate-menu {
    display: flex;
    justify-content: space-between;
    gap: toVw(22px);
    color: #ffffff;
    font-size: toVw(22px);
    font-weight: 100;
    li {
      a {
        cursor: pointer;
        font-size: toVw(22px);
        font-weight: 100;
        color: #ffffff;
      }
    }
  }
}
</style>
