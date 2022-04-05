<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="text column is-7">{{ task.task }}</div>
            <div class="column">
                <chronometer-task :timeInSeconds="task.timeInSeconds" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

import TaskInterface from '@/interface/TaskInterface'

import ChronometerTask from './ChronometerTask.vue'

export default defineComponent({
    name: 'TaskLabel',

    components: { ChronometerTask },

    props: {
        task: {
            type: Object as PropType<TaskInterface>,
            required: true,
        },
    },
})
</script>

<style lang="scss" scoped>
.box {
    background: #f8f9fa;
    .text {
        color: #414141;
    }
}
</style>
