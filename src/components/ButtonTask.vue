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

        handleTimer: {
            type: Function,
            default: () => 0,
        },
    },
})
</script>

<style lang="scss" scoped></style>
