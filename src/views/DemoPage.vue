<script setup lang="ts">
import TheFooter from '@/components/TheFooter.vue'
import TheHeader from '@/components/TheHeader.vue'
</script>

<template>
    <TheHeader />
    <div class="landing-wrapper">
      <div class="demo-txt">Audio.</div>
    </div>
    <TheFooter />
</template>

<style lang="scss" scoped>
.landing-wrapper {
    display: flex;
    min-height: calc(100vh - 200px);
    align-items: center;
    justify-content: center;
}

.demo-txt {
  color: $secondary;
  font-family: $sans-text;
  font-size:100px;
  font-weight: 600;

}
</style>
