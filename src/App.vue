<template>
    <main class="columns is-gapless is-multiline" :class="{ dark: darkMode }">
        <div class="column is-one-quarter">
            <side-bar @changingTheme="updateTheme" />
        </div>

        <div class="column is-three-quarter">
            <form-task @saveTask="saveTask" :class="{ dark: darkMode }" />
            <div class="p-5">
                <task-label v-for="(task, index) in tasks" :key="index" :task="task" />
                <task-box v-if="!tasks.length"> Você ainda não fez nenhuma tarefa hoje. </task-box>
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
import TaskBox from './components/TaskBox.vue'

export default defineComponent({
    name: 'App',

    components: {
        SideBar,
        FormTask,
        TaskLabel,
        TaskBox,
    },

    data() {
        return {
            tasks: [] as TaskInterface[],
            darkMode: false,
        }
    },

    methods: {
        saveTask(task: TaskInterface) {
            this.tasks.push(task)
        },

        updateTheme(darkMode: boolean) {
            this.darkMode = darkMode
        },
    },
})
</script>

<style lang="scss">
@import 'https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css';
@import '@/styles/theme.scss';

main {
    @include background-color($dark: false);
    &.dark {
        @include background-color($dark: true);
    }
}
</style>
