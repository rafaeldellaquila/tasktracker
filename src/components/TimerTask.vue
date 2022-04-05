<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
        <chronometer-task :timeInSeconds="timeInSeconds" />
        <div class="is-flex is-align-items-center">
            <button-task :icon="'ri-play-line'" title="play" :handleTimer="initCount" :timeSwitcher="timerOn" />
            <button-task :class="'ml-4'" :icon="'ri-stop-fill'" title="stop" :handleTimer="stopCount" :timeSwitcher="!timerOn" />
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import ButtonTask from './ButtonTask.vue'
import ChronometerTask from './ChronometerTask.vue'

export default defineComponent({
    name: 'TimerTask',

    components: { ChronometerTask, ButtonTask },

    emits: ['chronometerStopped'],

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
            this.$emit('chronometerStopped', this.timeInSeconds)
            this.timeInSeconds = 0
        },
    },
})
</script>

<style lang="scss" scoped></style>
