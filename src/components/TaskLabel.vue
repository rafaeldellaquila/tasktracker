<template>
    <task-box>
        <div class="columns">
            <div class="text column is-7">{{ task.task || 'Tarefa sem descrição' }}</div>
            <div class="column">
                <chronometer-task :timeInSeconds="task.timeInSeconds" />
            </div>
        </div>
    </task-box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

import TaskInterface from '@/interface/TaskInterface'

import ChronometerTask from './ChronometerTask.vue'
import TaskBox from './TaskBox.vue'

export default defineComponent({
    name: 'TaskLabel',

    components: { ChronometerTask, TaskBox },

    props: {
        task: {
            type: Object as PropType<TaskInterface>,
            required: true,
        },
    },
})
</script>

<style lang="scss" scoped></style>
