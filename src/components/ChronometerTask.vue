<template>
    <section>
        <strong class="timer">
            <i class="ri-timer-line" />
            {{ elapsedTime }}
        </strong>
    </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name: 'ChronometerTask',

    props: {
        timeInSeconds: {
            type: Number,
            default: 0,
        },
    },

    computed: {
        elapsedTime(): string {
            return new Date(this.timeInSeconds * 1000).toISOString().substring(11, 19)
        },
    },
})
</script>

<style lang="scss" scoped>
@import '@/styles/theme.scss';

.timer {
    color: $primary;
}
</style>
