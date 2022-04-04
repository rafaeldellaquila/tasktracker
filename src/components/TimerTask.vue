<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <chronometer-task :timeInSeconds="timeInSeconds" />
        <div class="is-flex is-align-items-center">
            <button class="button" @click="initCount" :disabled="timerOn">
                <i class="icon ri-play-line" />
                <span> play </span>
            </button>

            <button class="button ml-4" @click="stopCount" :disabled="!timerOn">
                <i class="icon ri-stop-fill" />
                <span> stop </span>
            </button>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from "vue"
import ChronometerTask from "./ChronometerTask.vue"
export default defineComponent({
    name: "TimerTask",

    components: { ChronometerTask },

    data() {
        return {
            timeInSeconds: 0,
            chronometer: 0,
            timerOn: false,
        }
    },

    methods: {
        initCount() {
            this.timerOn = true
            this.chronometer = setInterval(() => {
                this.timeInSeconds += 1
            }, 1000)
        },
        stopCount() {
            this.timerOn = false
            clearInterval(this.chronometer)
        },
    },
})
</script>

<style lang="scss" scoped></style>
