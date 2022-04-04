<template>
    <header class="is-flex is-justify-content-center p-4">
        <h1 class="mt-6"><img src="@/assets/logo.svg" alt="tasktracker logo"/></h1>
    </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
  name: 'SideBar',
});
</script>

<style lang="scss" scoped>
header {
    background: #414141;
    width: 100%;
    height: 100vh;

    @media only screen and (max-width: 768px) {
        padding: 2.5rem;
        height: auto;
    }
}


</style>