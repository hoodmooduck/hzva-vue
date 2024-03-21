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
        :style="'top:' + picture.top + 'px; ' +'left:' + picture.left + 'px;' +'transform: ' + transform"
    >
  </div>
</template>

<script>
export default {
  data() {
    return {
      transform: '',
    }
  },
  mounted() {
    this.transformChange();
  },
  methods: {
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