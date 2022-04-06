<template>
    <header class="is-flex is-align-items-center is-flex-direction-column p-4" :class="{ dark: this.darkMode }">
        <h1 class="mt-6 mb-6"><img src="@/assets/logo.svg" alt="tasktracker logo" /></h1>
        <button class="button" @click="changeTheme">{{ buttonText }}</button>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
export default defineComponent({
    name: 'SideBar',

    data() {
        return {
            darkMode: false,
        }
    },

    emits: ['changingTheme'],

    computed: {
        buttonText() {
            if (this.darkMode) return 'Desativar modo escuro'
            return 'Ativar modo escuro'
        },
    },

    methods: {
        changeTheme() {
            this.darkMode = !this.darkMode
            this.$emit('changingTheme', this.darkMode)
        },
    },
})
</script>

<style lang="scss" scoped>
@import '@/styles/theme.scss';

header {
    @include background-color($dark: true);
    width: 100%;
    height: 100vh;

    &.dark {
        @include background-color($dark: true);
        @include border($dark: true);
    }

    @media only screen and (max-width: 768px) {
        padding: 2.5rem;
        height: auto;
    }
}
</style>
