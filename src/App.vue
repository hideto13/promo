<script setup lang="ts">
import Gallery from './components/Gallery.vue';
</script>

<template>
  <div class="container">
    <Gallery />
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  height: 100%;
  position: fixed;
  perspective: 1500px;
}
</style>
