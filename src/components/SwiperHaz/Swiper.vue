<script setup>
import './Swiper.scss'
import SwiperCard from "@/components/SwiperHaz/SwiperCard/SwiperCard.vue";
</script>

<template>
  <div class="swiper-haz">
    <div class="container">
      <div class="swiper-haz__title title">Каждый из ребят очень <span class="pink-text">уникален</span> и привносит
        свою лепту в Хазяев
      </div>
      <div ref="compose" class="swiper-haz__compose">
        <div class="swiper-haz__wrapper">
          <div ref="swiper" class="swiper-wrapper">
            <div :key="data.id" v-for="data in cards" class="swiper-slide">
              <SwiperCard :card="data"/>
            </div>
          </div>
        </div>
      </div>
      <div :style="'min-height:'+ phantomHeights +'px'" class="phantom"></div>
    </div>
  </div>
</template>

<script>
import listPersons from "@/components/SwiperHaz/CardListHaz.js";
import Swiper from "swiper";
import {Scrollbar} from "swiper/modules";
import {ref} from "vue";

export default {
  data() {
    return {
      cards: listPersons,
      phantomHeights: 0,
      scrollTop: 0,
      scrolling: false,
      count_top: 0,
    }
  },
  mounted() {
    this.phantomHeights = this.$refs.swiper.offsetHeight
    if (window.innerWidth <= 1224) return
    const swiper = document.querySelector('.swiper-haz__wrapper')
    const slider = new Swiper(swiper, {
      slidesPerView: "auto",
      direction: 'vertical',
      speed: 1500,
      mousewheel: {
        sensitivity: 1,
      },
      allowTouchMove: false,
      modules: [Scrollbar],
      scrollbar: {
        draggable: true
      }
    })
    document.addEventListener('scroll', (e) => {
      const swiperRect = this.$refs.swiper.getBoundingClientRect();
      this.scrollTop = document.documentElement.scrollTop;
      this.scrolling = document.documentElement.scrollTop > this.scrollTop;

    })
  }
}
</script>
