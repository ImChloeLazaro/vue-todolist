<script>
import TaskStatusCount from './TaskStatusCount.vue';
export default {
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    computed: {
        todo() {
            return this.tasks.filter(task => !task.done).length
        },
        done() {
            return this.tasks.filter(task => task.done).length
        }
    },
    components: {
        TaskStatusCount
    },    
}
</script>
<template>
    <div>
        <TaskStatusCount status="todo" :count="todo" />
        <TaskStatusCount status="done" :count="done" />
    </div>
</template>