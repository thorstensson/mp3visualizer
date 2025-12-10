<script setup lang="ts">
import CommonFooter from "@/components/common/CommonFooter.vue"
import MediaAudioPlayer from "@/components/media/MediaAudioPlayer.vue"
</script>

<template>
  <div class="page-container">
    <div class="lab-wrapper">
      <MediaAudioPlayer />
    </div>
    <CommonFooter
      info="© 2025 Thomas Thorstensson •"
      link="https://github.com/thorstensson"
      linkLabel="GitHub"
    />
  </div>
</template>

<style lang="scss" scoped>
.page-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  min-height: 100dvh; /* Use dynamic viewport height for better mobile support */
}

.lab-wrapper {
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center;
  min-height: calc(100vh - 50px); // Ensure minimum height minus footer height
  min-height: calc(
    100dvh - 50px
  ); /* Use dynamic viewport height for better mobile support */
}
</style>
