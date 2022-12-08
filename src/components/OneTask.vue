<script>
export default {
    name: 'OneTask',
    props: {
        task: Object
    },
    methods: {
        onDelete(id) {
            this.$emit(`delete-task`, id)
            // we need to emit upwards into the app.vue; this(what called the method).$emit("event with custom name", passing the id of the task that called the method as a parameter )
            // emits always one level up -> into Tasks.vue
        }
    },
}

</script>



<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'oneTask']">
        <!--if task.reminder is true then name of the class = .oneTask.reminder / if false then class= .oneTask-->
        <h3>{{ task.text }} <i @click="onDelete(task.id)" class="fas fa-times"></i> </h3>
        <p>{{ task.day }}</p>
    </div>
</template>




<style scope>
.fas {
    color: red;
}

.oneTask {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}

.oneTask.reminder {
    border-left: 5px solid green;
}

.oneTask h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>