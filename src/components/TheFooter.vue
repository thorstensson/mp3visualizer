<script setup lang="ts">
import TheHeaderFooterSlot from '@/components/TheHeaderFooterSlot.vue'
import AudioPlayer from '@/components/AudioPlayer.vue'
</script>

<template>
  <div class="footer-wrapper">
    <TheHeaderFooterSlot>
      <template #social>
       Thomas Thorstensson
      </template>
      <template #player>
        <AudioPlayer />
      </template>
    </TheHeaderFooterSlot>
  </div>
</template>

<style lang="scss" scoped>
.footer-wrapper {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  height: 100px;
  padding: 0 $page-hpad $page-vpad $page-hpad;
  font-family: $sans-text;
  font-weight: 500;
}
</style>
