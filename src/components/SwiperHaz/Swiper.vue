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
      <div ref="compose" :style="'height:'+ phantomHeights +'px'" class="swiper-haz__compose">
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
      scrollBottom: 0
    }
  },
  mounted() {
    this.phantomHeights = this.$refs.swiper.offsetHeight * 2
    if (window.innerWidth <= 1224) return
    const swiper = document.querySelector('.swiper-haz__wrapper')
    const slider = new Swiper(swiper, {
      slidesPerView: "auto",
      direction: 'vertical',
      speed: 1000,
      mousewheel: {
        sensitivity: 1,
      },
      allowTouchMove: false,
      modules: [Scrollbar],
      scrollbar: {
        draggable: true
      }
    })
    window.addEventListener('wheel', (e) => {
      const swiperRect = this.$refs.swiper.getBoundingClientRect();
      if (swiperRect.top <= 101) {
        if(e.deltaY > 0) {
          ++this.scrollTop
          if(this.scrollTop < 5) return
          this.scrollTop = 0
          slider.slideNext()
        } else{
          ++this.scrollBottom
          if(this.scrollBottom < 4) return
          this.scrollBottom = 0
          slider.slidePrev()
        }
      } else {
      }
    })
  }
}
</script>
