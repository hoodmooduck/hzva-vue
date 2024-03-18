<script setup>
  import './BurgerMenu.scss'
</script>

<template>
  <div :class="!props.modalState ? 'burger-menu' : 'burger-menu burger-menu--active' ">
    <a v-for="link in props.links" :key="link.id" :href="link.path" class="burger-menu__link header__link">{{link.name}}</a>
  </div>
</template>
<script>
export default {
  props: ['props'],
};
</script>