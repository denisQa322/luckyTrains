<template>
  <div class="slider-item">
    <div class="slider-item__title">{{ item.title }}</div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import { ISliderItem } from "@/types/sliderItem";

@Component({
  props: {
    item: {
      type: Object as () => ISliderItem,
      required: true,
    },
  },
})
export default class SliderItemComponent extends Vue {}
</script>

<style scoped lang="scss"></style>
