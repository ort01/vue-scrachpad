<script>
import Button from "./Button.vue"

export default {
    name: "Header",
    props: {
        text: String,
        addTaskButtonState: Boolean
    },
    components: {
        Button
    }
}
</script>


<template>
    <header>
        <h1> {{ text }}</h1>
        <Button @btn-click="$emit('toggle-add-task')" :text="addTaskButtonState ? 'Close' : 'Add Task'"
            :color="addTaskButtonState ? 'red' : 'green'" />
    </header>
</template>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
}
</style>