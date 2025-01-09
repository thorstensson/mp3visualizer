<script setup lang="ts">
import TheFooter from '@/components/TheFooter.vue'
import TheHeader from '@/components/TheHeader.vue'
</script>

<template>
    <TheHeader />
    <div class="landing-wrapper">
    </div>
    <TheFooter />
</template>

<style lang="scss" scoped>
.landing-wrapper {
    display: flex;
    min-height: calc(100vh - 200px);
}
</style>
