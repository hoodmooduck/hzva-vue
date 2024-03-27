<script setup>
  import './Header.scss'
  import HeaderLogo from './HeaderLogo/HeaderLogo.vue'
  import HeaderLinks from "@/components/Header/HeaderLinks/HeaderLinks.vue";
  import BurgerMenu from "@/components/BurgerMenu/BurgerMenu.vue";
</script>

<template>
  <header class="header">
    <div class="container">
      <div class="header__wrapper">
        <HeaderLogo />
        <HeaderLinks :props="props.links"/>
        <div @click="openModal" :class="!modal ? 'header__button' : 'header__button header__button--open'">
          <span class="header__span"></span>
          <span class="header__span"></span>
        </div>
      </div>
    </div>
  </header>
  <BurgerMenu :props="props"/>
</template>

<script>
  import {ref} from "vue";

  let modal = ref(false)
  const openModal = () => {
    modal.value = !modal.value;
  };
  export default {
    data() {
      return {
        props: {
          links: [
            {id:1, name: 'Кто такие Хазяева?', path: '/'},
            {id:2, name: 'Популярность', path: '/'},
            {id:3, name: 'Игры', path: '/'},
            {id:4, name: 'Мерч', path: '/'},
          ],
          modalState: modal
        },
      }
    },
    mounted() {

    }
  }
</script>