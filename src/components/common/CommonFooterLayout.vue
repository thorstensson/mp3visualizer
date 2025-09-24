<script setup lang="ts">
import { useSlots } from "vue";

const slots = useSlots();
</script>

<template>
  <div v-if="slots.social" class="social">
    <slot name="social"></slot>
  </div>
</template>

<style scoped lang="scss">
.social {
  font-family: $sans-text;
  font-size: 16px;
  color: $accent2;
  user-select: none;
}
</style>
