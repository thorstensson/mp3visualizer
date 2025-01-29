<script setup lang="ts">
import DemoPage from '@/views/DemoPage.vue';
</script>

<template>
  <DemoPage />
</template>

<style lang="scss">
html,
body {
  background-color: $primary;
  margin: 0;
  overflow-x: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-font-smoothing: antialiased;
  -o-font-smoothing: antialiased;
  overscroll-behavior: none;
}

body {
  min-height: 100vh;
}
</style>
