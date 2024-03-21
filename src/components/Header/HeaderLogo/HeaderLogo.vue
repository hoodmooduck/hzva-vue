<template>
  <div class="header__logo">
    <div class="header__eyes">
      <svg :style="{position: 'relative'}" width="19" height="16" viewBox="0 0 19 16" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path d="M2.72858 0.711571H18.0581L16.1776 15.9076H0.848145L2.72858 0.711571Z"
              fill="white"/>
        <path
            :style="{position: 'absolute', transition: `.2s`, transform: `translate(${checkMousePositionX}px, ${checkMousePositionY}px)` }"
            class="eye" d="M8.48937 4.99749H15.172L14.3524 11.6211H7.66968L8.48937 4.99749Z" fill="black"/>
      </svg>
      <svg width="19" height="16" viewBox="0 0 19 16" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path :style="{position: 'relative'}" d="M2.72858 0.711571H18.0581L16.1776 15.9076H0.848145L2.72858 0.711571Z"
              fill="white"/>
        <path
            :style="{position: 'absolute', transition: `.2s`, transform: `translate(${checkMousePositionX}px, ${checkMousePositionY}px)` }"
            class="eye" d="M8.48937 4.99749H15.172L14.3524 11.6211H7.66968L8.48937 4.99749Z" fill="black"/>
      </svg>
    </div>
    <picture class="header__image">
      <img src="@/assets/images/logo.png" alt="logo">
    </picture>
  </div>
</template>

<script setup>
  import {ref} from 'vue';

  const checkMousePositionX = ref(-6);
  const checkMousePositionY = ref(-7);
  const xMax = 3;
  const yMax = 4;
  window.addEventListener('mousemove', (e) => moveEye(e))
  const moveEye = (e) => {
    const pupil = document.querySelectorAll('.eye');
    let y = e.clientY - 55;
    let x = e.clientX - pupil[0].getBoundingClientRect().x;

    checkMousePositionX.value = x > 29 ? xMax : (x < -6 ? -xMax-2 : xMax / 2);
    checkMousePositionY.value = y > 3 ? yMax : (y < -7 ? -yMax : yMax / 2);
  };
</script>