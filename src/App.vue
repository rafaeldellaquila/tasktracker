<template>
    <main class="columns is-gapless is-multiline">
        <div class="column is-one-quarter">
            <side-bar />
        </div>

        <div class="column is-three-quarter">
            <form-task />
        </div>
    </main>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import SideBar from "@/components/SideBar.vue"
import FormTask from "@/components/FormTask.vue"

export default defineComponent({
    name: "App",
    components: {
        SideBar,
        FormTask,
    },
})
</script>

<style lang="scss">
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css";
</style>
