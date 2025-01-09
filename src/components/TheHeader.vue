<script setup lang="ts">
import TheHeaderFooterSlot from '@/components/TheHeaderFooterSlot.vue'
</script>

<template>
    <div class="header-wrapper">
        <TheHeaderFooterSlot>
            <template #social>
                Compact player demo &#128498;
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
    padding: 10px $page-lpad 0 $page-lpad;
}

.logo {
    width: 90px;
}
</style>
