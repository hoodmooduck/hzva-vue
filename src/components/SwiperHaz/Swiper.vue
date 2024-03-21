<script setup>
  import './Swiper.scss'
  import SwiperCard from "@/components/SwiperHaz/SwiperCard/SwiperCard.vue";
</script>

<template>
  <div class="swiper-haz">
    <div class="container">
      <div class="swiper-haz__wrapper">
        <div class="swiper-wrapper">
          <div :key="data.id" v-for="data in props.cards" class="swiper-slide">
            <SwiperCard :card="data"/>
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

  export default {
    data () {
      return {
        props: {
          cards: listPersons
        }
      }
    },
    // mounted() {
    //   if(window.innerWidth <= 1224) return
    //   const swiper = document.querySelector('.swiper-haz__wrapper')
    //   const slider = new Swiper(swiper, {
    //     slidesPerView: "auto",
    //     direction: 'vertical',
    //     mousewheel: {
    //       sensitivity: 1,
    //     },
    //     allowTouchMove: true,
    //     modules: [Scrollbar],
    //     scrollbar: {
    //       draggable: true
    //     }
    //   })
    //
    //   const observer = new IntersectionObserver((entries) => {
    //     entries.forEach((entry) => {
    //       if (entry.isIntersecting) {
    //         window.addEventListener('scroll',(e) => {
    //           console.log(e)
    //         })
    //       }
    //     });
    //   });
    //
    //   observer.observe(swiper)
    // }
  }
</script>
