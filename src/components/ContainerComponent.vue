<template>
  <div class="container" :class="styleType">
    <template>
      <slot></slot>
    </template>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
export enum ContainerType {
  FLEX_BETWEEN = "flex-between",
  GRID = "grid",
}

@Component({
  props: {
    styleType: String as () => ContainerType,
  },
})
export default class ContainerComponent extends Vue {
  styleType: string | undefined;
}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.container {
  width: toVw(1400px);
  margin: auto;
}
.container.flex-between {
  display: flex;
  justify-content: space-between;
}
.container.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(toVw(610px), 1fr));
  grid-gap: toVw(90px);
}
</style>
