<template>
    <button class="button" @click="handleTimer" :disabled="timeSwitcher">
        <i class="icon" :class="icon" />
        <span> {{ title }} </span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name: 'ButtonTask',

    emits: ['handleTimer'],

    props: {
        title: {
            type: String,
            default: '',
        },

        icon: {
            type: String,
            default: '',
        },

        classes: {
            type: String,
            default: '',
        },

        timeSwitcher: {
            type: Boolean,
            default: false,
        },
    },

    methods: {
        handleTimer(): void {
            this.$emit('handleTimer')
        },
    },
})
</script>

<style lang="scss" scoped>
@import '@/styles/theme.scss';

button {
    color: $primary;
    border-color: $primary;

    &.dark {
        @include background-color($dark: true);
    }

    &:disabled {
        color: $gray;
        border-color: $gray;
    }
}
</style>
