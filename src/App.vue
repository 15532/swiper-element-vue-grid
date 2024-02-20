<!-- https://swiperjs.com/demos#grid -->

<script setup lang="ts">
// import function to register Swiper custom elements
import { register } from 'swiper/element/bundle'
import { onMounted } from 'vue'

// register Swiper custom elements
register()

onMounted(() => {
  const swiperEl = document.querySelector('swiper-container')!

  const params = {
    pagination: {
      clickable: true,
    },
    slidesPerView: 3,
    grid: {
      rows: 2,
      // fill: 'row',
    },
    spaceBetween: 30,
    keyboard: {
      enabled: true,
    },

    // array with CSS styles
    injectStyles: [
      `
      :host {
        width: 100%;
        height: 100%;
        margin-left: auto;
        margin-right: auto;
      }
      `,
      `
      ::slotted(swiper-slide) {
        text-align: center;
        font-size: 18px;
        background: #fff;
        height: calc((100% - 30px) / 2) !important;
        display: flex;
        justify-content: center;
        align-items: center;
      }
      `,
    ],

    // array with CSS urls
    // injectStylesUrls: ['path/to/one.css', 'path/to/two.css'],
  }

  Object.assign(swiperEl, params)

  swiperEl.initialize()
})
</script>

<template>
  <swiper-container class="mySwiper" :init="false">
    <swiper-slide v-for="n in 9" :key="n">
      {{ `Slide ${n}` }}
    </swiper-slide>
  </swiper-container>
</template>

<style>
#app {
  height: 100%;
}

html,
body {
  position: relative;
  height: 100%;
}

body {
  background: #eee;
  font-family:
    Helvetica Neue,
    Helvetica,
    Arial,
    sans-serif;
  font-size: 14px;
  color: #000;
  margin: 0;
  padding: 0;
}
</style>
