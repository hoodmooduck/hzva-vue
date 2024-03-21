<script setup>

import SwiperCard from "@/components/SwiperHaz/SwiperCard/SwiperCard.vue";
</script>

<template>
  <div class="swiper-haz">
    <div class="container">
      <div class="swiper-haz__wrapper">
        <SwiperCard :key="data.id" v-for="data in props.cards" :card="data"/>
      </div>
    </div>
  </div>
</template>

<script>
  import listPersons from "@/components/SwiperHaz/CardListHaz.js";

  export default {
    data () {
      return {
        props: {
          cards: listPersons
        }
      }
    },
    mounted() {
      console.log(this.props.cards)
    }
  }
</script>