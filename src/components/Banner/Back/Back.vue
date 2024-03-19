<script setup>
  import './Back.scss'
  import pictures from "./images.js";
</script>

<template>
  <div class="banner__image-collection">
    <img
        v-for="picture in pictures"
        :src="'/src/assets/images/Banner/'+ picture.img +'.webp'"
        :alt="picture.img"
        :style="'top:' + picture.top + 'px; left:' + picture.left + 'px'"
    >
  </div>
</template>

<script>

</script>