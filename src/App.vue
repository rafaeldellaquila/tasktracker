<template>
    <main class="columns is-gapless is-multiline">
        <div class="column is-one-quarter">
            <side-bar />
        </div>

        <div class="column is-three-quarter">
            <form-task @saveTask="saveTask" />
            <div class="p-5">
                <task-label v-for="(task, index) in tasks" :key="index" :task="task" />
            </div>
        </div>
    </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TaskInterface from '@/interface/TaskInterface'

import SideBar from '@/components/SideBar.vue'
import FormTask from '@/components/FormTask.vue'
import TaskLabel from './components/TaskLabel.vue'

export default defineComponent({
    name: 'App',

    components: {
        SideBar,
        FormTask,
        TaskLabel,
    },

    data() {
        return {
            tasks: [] as TaskInterface[],
        }
    },

    methods: {
        saveTask(task: TaskInterface) {
            this.tasks.push(task)
        },
    },
})
</script>

<style lang="scss">
@import 'https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css';
</style>
