<template>
    <div class="box has-text-weight-bold">
        <slot />
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'TaskBox',
})
</script>

<style lang="scss" scoped>
.box {
    background: #f8f9fa;
    .text {
        color: #414141;
    }
}
</style>
