<script setup>
  import './SwiperCard.scss'
</script>

<template>
  <div class="swiper-card">
    <div class="swiper-card__content">
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
    <picture class="swiper-card__image">
      <img src="../../../assets/images/Swiper/Exile.webp" />
    </picture>
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