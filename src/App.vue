<template>
  <div id="app">
    <HeaderComponent />
    <router-view />
    <FooterComponent />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HeaderComponent from "@/components/HeaderComponent.vue";
import FooterComponent from "./components/FooterComponent.vue";

@Component({
  components: {
    HeaderComponent,
    FooterComponent,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Exo:wght@100;200;300;400;500;600;700;800;900&display=swap");
@import "@/assets/scss/toVw.scss";
@import "@/assets/scss/media.scss";
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  font-family: sans-serif, "Exo";
}
header {
  width: 100%;
}
a {
  text-decoration: none;
  color: black;
}
ul {
  list-style-type: none;
}
</style>
