<script setup>
import './Banner.scss'
import Back from './Back/Back.vue'
</script>

<template>
  <div class="banner">
    <div class="banner__back">
      <Back/>
    </div>
    <div class="banner__wrapper">
      <h1 class="banner__title title">
        Стрим идет <br> Хазяева<span class="banner__substrate">едут</span>
      </h1>
      <div class="banner__arrow"></div>
    </div>
  </div>
</template>