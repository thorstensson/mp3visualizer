<script setup lang="ts">
import CommonFooter from "@/components/common/CommonFooter.vue";
import MediaAudioPlayer from "@/components/media/MediaAudioPlayer.vue";
</script>

<template>
  <div class="page-container">
    <div class="lab-wrapper">
      <MediaAudioPlayer />
    </div>
    <CommonFooter />
  </div>
</template>

<style lang="scss" scoped>
.page-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.lab-wrapper {
  display: flex;
  flex: 1;
  align-items: center;
  justify-content: center;
}

.demo-txt {
  color: $secondary;
  font-family: $sans-text;
  font-size: 100px;
  font-weight: 600;
  position: absolute;
  z-index: 10;
}
</style>
