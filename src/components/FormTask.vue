<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="task" />
            </div>

            <div class="column">
                <timer-task @chronometerStopped="endTask" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TimerTask from './TimerTask.vue'
export default defineComponent({
    name: 'FormTask',

    components: { TimerTask },

    emits: ['saveTask'],

    data() {
        return {
            task: '',
        }
    },

    methods: {
        endTask(elapsedTimeCount: number): void {
            this.$emit('saveTask', {
                timeInSeconds: elapsedTimeCount,
                task: this.task,
            })
            this.task = ''
        },
    },
})
</script>

<style lang="scss" scoped>
input {
    color: #414141;
    &:focus {
        border-color: #ea798e;
        box-shadow: none;
    }
}
</style>
