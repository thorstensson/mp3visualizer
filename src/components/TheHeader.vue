<script setup lang="ts">
import TheHeaderFooterSlot from '@/components/TheHeaderFooterSlot.vue'
</script>

<template>
  <div class="header-wrapper">
    <TheHeaderFooterSlot>
      <template #social>
        Compact player demo
      </template>
    </TheHeaderFooterSlot>
  </div>
</template>

<style lang="scss" scoped>
.header-wrapper {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  height: 100px;
  padding: $page-vpad $page-hpad 0 $page-hpad;
}

.logo {
  width: 90px;
}
</style>
