<script setup lang="ts">
import VuePictureSwipe from 'vue3-picture-swipe'

const items = [{
  src: 'http://via.placeholder.com/1200x800',
  thumbnail: 'http://via.placeholder.com/600x400',
  w: 600,
  h: 400,
},
{
  src: 'http://via.placeholder.com/1200x800',
  thumbnail: 'http://via.placeholder.com/600x400',
  w: 600,
  h: 400,
},
{
  src: 'http://via.placeholder.com/1200x800',
  thumbnail: 'http://via.placeholder.com/600x400',
  w: 600,
  h: 400,
},
{
  src: 'http://via.placeholder.com/1200x800',
  thumbnail: 'http://via.placeholder.com/600x400',
  w: 600,
  h: 400,
}]
</script>

<template>
  <vue-picture-swipe :items="items" />
</template>

<style>
.my-gallery {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>

<route lang="yaml">
meta:
  layout: detail
</route>
