<script setup lang="ts">
import CommonFooterLayout from "@/components/common/CommonFooterLayout.vue";
</script>

<template>
  <div class="footer-wrapper">
    <CommonFooterLayout>
      <template #social> S3 + Web Audio API + P5.js </template>
    </CommonFooterLayout>
  </div>
</template>

<style lang="scss" scoped>
.footer-wrapper {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  height: 50px;
  padding: 0 $page-hpad $page-vpad $page-hpad;
  flex-shrink: 0; /* Prevent footer from shrinking */
  
  // Ensure footer is always visible on mobile
  @media (max-width: 768px) {
    position: relative;
    z-index: 100;
    background-color: $primary;
  }
}
</style>
