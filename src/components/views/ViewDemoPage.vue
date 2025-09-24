<script setup lang="ts">
import CommonFooter from "@/components/common/CommonFooter.vue";
import MediaAudioPlayer from "@/components/media/MediaAudioPlayer.vue";
</script>

<template>
  <div class="lab-wrapper">
    <MediaAudioPlayer />
  </div>
  <CommonFooter />
</template>

<style lang="scss" scoped>
.lab-wrapper {
  display: flex;
  min-height: calc(100vh - 100px);
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
