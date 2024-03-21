<script setup>

</script>

<template>
  <div class="swiper-card">
    <p class="swiper-card__name">{{ card.nickName }}</p>
    <p class="swiper-card__description">
      {{ card.fullName[0] }}
      <span v-if="card.fullName[1]" class="pink-text">
        {{ card.fullName[1] }}
      </span>
    </p>
    <p class="swiper-card__text">{{ card.description }}</p>
    <div class="swiper-card__social">
    </div>
  </div>
</template>

<script>
export default {
  props: {
    card: {
      type: Object,
      default: () => {
      }
    }
  }
}
</script>