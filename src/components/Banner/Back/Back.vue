<script setup>
import './Back.scss'
import pictures from "./images.js";
</script>

<template>
  <div class="banner__image-collection">
    <div class="banner__image-wrapper">
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="picture in pictures">
          <img
              :src="'/assets/images/Banner/'+ picture.img +'.webp'"
              :alt="picture.img"
          >
        </div>
        <div class="swiper-slide">
          <img
              class="image__hidden"
              src="/assets/images/Banner/fb_24.webp"
              alt="fb_24"
          >
        </div>
      </div>
    </div>
    <div class="banner__image-wrapper">
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="picture in pictures">
          <img
              :src="'/assets/images/Banner/'+ picture.img +'.webp'"
              :alt="picture.img"
          >
        </div>
        <div class="swiper-slide">
          <img
              class="image__hidden"
              src="/assets/images/Banner/fb_24.webp"
              alt="fb_24"
          >
        </div>
      </div>
    </div>
    <img
        v-if="!wind"
        v-for="picture in pictures"
        :src="'/assets/images/Banner/'+ picture.img +'.webp'"
        :alt="picture.img"
        :style="'top:' + picture.top + 'px; ' +'left:' + picture.left + 'px;' +'transform: ' + transform"
    >
  </div>
</template>

<script>
import Swiper from "swiper";
import {Autoplay} from "swiper/modules";

export default {
  data() {
    return {
      transform: '',
      wind: false,
    }
  },
  mounted() {
    this.transformChange();
    this.checkWindowSize();
    window.addEventListener('resize', () => this.checkWindowSize())

    const swiper = document.querySelectorAll('.banner__image-wrapper')
    swiper.forEach((el, idx) => {
      const slider = new Swiper(el, {
        slidesPerView: "auto",
        loop: true,
        modules: [Autoplay],
        speed: 7500,
        spaceBetween: 72,
        autoplay: {
          delay: 0,
          reverseDirection: idx === 0
        }
      })
    })
  },
  methods: {
    checkWindowSize() {
      if (window.innerWidth <= 1224) {
        this.wind = true
      } else {
        this.wind = false
      }
    },
    transformChange() {
      window.addEventListener('mousemove', (e) => {
        if (document.documentElement.offsetWidth > 1215) {
          let x = e.x;
          let y = e.y;
          this.transform = `translateX(${(x) / 100}%) translateZ(${0}px) translateY(${(y) / 100}%)`;
        }
      })
    }
  }
}
</script>