<template>
  <div class="menu">
    <ul class="menu_list">
      <li>
        <a href="/">Главная</a>
      </li>
      <router-link tag="li" to="/about">О компании</router-link>
      <router-link tag="li" to="/services">Наши услуги</router-link>
      <router-link tag="li" to="/clients">Клиентам</router-link>
      <router-link tag="li" to="/contacts">Контакты</router-link>
      <router-link tag="li" to="/vacancies">Вакансии</router-link>
    </ul>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class MenuComponent extends Vue {}
</script>

<style scoped lang="scss">
@import "@/assets/scss/toVw.scss";
.menu {
  display: flex;
  align-items: center;
  &_list {
    display: flex;
    justify-content: space-between;
    gap: toVw(30px);
    color: #103f7c;
    font-size: toVw(15px);
    font-family: "Exo";
    cursor: pointer;
    a {
      li {
        font-size: toVw(15px);
      }
    }
  }
}
</style>
