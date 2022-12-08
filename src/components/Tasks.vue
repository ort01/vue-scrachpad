
<script>
import OneTask from './OneTask.vue'

export default {
    name: 'Tasks',
    props: {
        tasks: Array // arrayOfTasks []
    },
    components: {
        OneTask
    },
    emits: ['delete-task', 'toggle-reminder'], //array of event that we are emiting
}
</script>




<template>
    <div :key="eachTask.id" v-for="eachTask in tasks" class="tasks">
        <!-- v-for is an for loop for tasks(arrayOfTasks) and represents each item from array as "task" -->
        <OneTask @toggle-reminder="$emit('toggle-reminder', $event)" @delete-task="$emit('delete-task', $event)"
            :task="eachTask" />
        <!--when @delete-task happens, emit the event with an id, that triggered the event-->
        <!--task from v-for="eachTask in tasks"-->
    </div>
</template> 




<style>

</style>