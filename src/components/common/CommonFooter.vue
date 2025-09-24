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
  height: 100px;
  padding: 0 $page-hpad $page-vpad $page-hpad;
}
</style>
