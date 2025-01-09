<script setup lang="ts">
import { useSlots } from 'vue'

const slots = useSlots()
</script>

<template>
  <div v-if="slots.social" class="social">
    <slot name="social"></slot>
  </div>
  <div v-if="slots.player" class="player">
    <slot name="player"></slot>
  </div>
</template>

<style scoped lang="scss">
.social {
  font-family: $sans-text;
  font-optical-sizing: $sans-ui-optic;
  font-size: 16px;
  color: $clr-secondary;
}
</style>
