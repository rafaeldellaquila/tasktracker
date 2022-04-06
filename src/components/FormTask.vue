<template>
    <div class="box" :class="{ darkClassTask }">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" v-model="task" />
            </div>

            <div class="column">
                <timer-task @chronometerStopped="endTask" :class="{ darkClassTask }" />
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
@import '@/styles/theme.scss';

.box {
    @include background-color($dark: false);
    input {
        color: $secondary;
        &:focus {
            border-color: $primary;
            box-shadow: none;
        }
    }

    &.dark {
        @include background-color($dark: true);
        input {
            @include background-color($dark: true);
            &::placeholder {
                color: $white;
            }
        }
    }
}
</style>
