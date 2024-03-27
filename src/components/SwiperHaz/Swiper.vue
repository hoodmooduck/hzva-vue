<script setup>
import './Swiper.scss'
import SwiperCard from "@/components/SwiperHaz/SwiperCard/SwiperCard.vue";
</script>

<template>
  <div class="swiper-haz">
    <div class="container">
      <div class="swiper-haz__title title wow fadeInUp" data-wow-duration="1s">Каждый из ребят очень <span class="pink-text">уникален</span> и привносит
        свою лепту в Хазяев
      </div>
      <div :style="'height:'+ phantomHeights +'px'" ref="compose" class="swiper-haz__compose">
        <div class="swiper-haz__wrapper">
          <div ref="swiper" class="swiper-wrapper">
            <div :key="data.id" v-for="data in cards" class="swiper-slide">
              <SwiperCard :card="data"/>
            </div>
          </div>
        </div>
      </div>
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
      count_top: 0,
      activeSlide: 0,
    }
  },
  mounted() {
    document.documentElement.scrollTo(0,0)
    const swiper = document.querySelector('.swiper-haz__wrapper')
    const slider = new Swiper(swiper, {
      slidesPerView: "auto",
      direction: window.innerWidth <= 1224 ? "horizontal" : "vertical",
      speed: 1500,
      resizeObserver: true,
      mousewheel: {
        sensitivity: 1,
      },
      allowTouchMove: window.innerWidth <= 1224,
    })
    this.phantomHeights = slider.slides.length * 701 + 350
    ;
    this.scrollTop = this.$refs.swiper.getBoundingClientRect().top;

    if (window.innerWidth <= 1224) {
      this.phantomHeights = 'auto'
      return
    }
    document.addEventListener('scroll', (e) => {
      console.log(window.innerWidth)
        const top = this.$refs.swiper.getBoundingClientRect().top
        let index = Math.round((document.documentElement.scrollTop - this.scrollTop - 350) / 700);
        if(index === this.activeSlide) return
        this.activeSlide = index
        slider.slideTo(this.activeSlide)
    })
  }
}
</script>
