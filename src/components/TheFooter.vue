<script setup lang="ts">
import TheHeaderFooterSlot from '@/components/TheHeaderFooterSlot.vue'
import MinimlAudioPlayer from '@/components/MinimlAudioPlayer.vue'
</script>

<template>
  <div class="footer-wrapper">
    <TheHeaderFooterSlot>
      <template #social>
        <a target='_blank' href='https://www.linkedin.com/in/thomasthorstensson'>Discord</a><br>
        <a target='_blank' href='https://www.flickr.com/photos/thomasthorstensson/'>Flickr</a>
      </template>
      <template #player>
        <MinimlAudioPlayer />
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
  padding: 0 $page-lpad 10px $page-lpad;
}
</style>
