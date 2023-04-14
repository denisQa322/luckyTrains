<template>
  <div class="buttons">
    <div class="slider-buttons__wrapper">
      <div class="slider-buttons" v-if="showControls">
        <button
          :disabled="disabledLeft"
          @click="arrowLeftClickHandler()"
          class="btn-left"
        >
          <img src="../../assets/icons/arrow-left.svg" alt="" />
        </button>
        <button
          :disabled="disabledRight"
          @click="arrowRightClickHandler()"
          class="btn-right"
        >
          <img src="../../assets/icons/arrow-right.svg" alt="" />
        </button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({
  props: {
    showControls: {
      type: Boolean,
      required: false,
    },
    disabledLeft: {
      type: Boolean,
      default: false,
    },
    disabledRight: {
      type: Boolean,
      default: false,
    },
  },
})
export default class SliderButtonsComponent extends Vue {
  disabledRight: boolean | undefined;
  disabledLeft: boolean | undefined;
  arrowLeftClickHandler() {
    this.$emit("arrowLeftClickHandler");
  }
  arrowRightClickHandler() {
    this.$emit("arrowRightClickHandler");
  }
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.slider-buttons {
  gap: toVw(15px);
  display: flex;
  align-items: center;
  position: absolute;
  top: toVw(148px);
  left: toVw(279px);
  z-index: 100;
  button {
    padding: toVw(11px) toVw(13px);
    width: toVw(32px);
    height: toVw(32px);
    background-color: #ff1515;
    border-radius: toVw(7px);
    border: none;
    display: flex;
    align-items: center;
    cursor: pointer;
    img {
      width: toVw(10px);
      height: toVw(6px);
    }
    &[disabled] {
      background-color: rgba(255, 255, 255, 0.5);
    }
  }
}
</style>
