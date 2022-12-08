<script>
export default {
    name: 'AddTask',
    data() { // creating an object with attributes that are binded with inputs through v-model="name of the attribute"
        return {
            text: '',
            day: '',
            reminder: false,
        }
    },
    methods: {
        onSubmit(event) {
            event.preventDefault()


            if (!this.text) {
                alert('Please add a task')
                return
            }

            const newTask = {
                id: Math.floor(Math.random() * 1000),
                text: this.text,
                day: this.day,
                reminder: this.reminder,
            }

            this.$emit('add-task', newTask) // newTask is a const that is passed as an argument to addTask(newTask)
            // component AddTask.vue in App.vue with emit === <AddTask @add-task="addTask" />; on @add-task call addTask() method
            // method onSubmit() in AddTask.vue calls addTask() in App.vue with argument newTask === addTask(newTask) {this.arrayOfTasks = [...this.arrayOfTasks, newTask]},

            this.text = ''
            this.day = ''
            this.reminder = false
        }
    }
}
</script>





<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
            <!-- v-model="text" ===> binding the input with data -->
        </div>
        <div class="form-control">
            <label>Day & Time</label>
            <input type="text" v-model="day" name="day" placeholder="Add Day & Time" />
        </div>
        <div class="form-control form-control-check">
            <label>Set Reminder</label>
            <input type="checkbox" v-model="reminder" name="reminder" />
        </div>

        <input type="submit" value="Save Task" class="btn btn-block" />
    </form>
</template>






<style scoped>
.add-form {
    margin-bottom: 40px;
}

.form-control {
    margin: 20px 0;
}

.form-control label {
    display: block;
}

.form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 17px;
}

.form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.form-control-check label {
    flex: 1;
}

.form-control-check input {
    flex: 2;
    height: 20px;
}
</style>

