<template>
    <div class="box has-text-weight-bold dark">
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
@import '@/styles/theme.scss';

.box {
    @include background-color($dark: false);

    .text {
        color: $secondary;
    }
}
</style>
