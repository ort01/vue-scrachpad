<script>
import Header from "./components/Header.vue"
import Tasks from "./components/Tasks.vue"
import AddTask from "./components/AddTask.vue"

export default {
    name: "App",
    components: {
        Header,
        Tasks,
        AddTask
    },
    data() {
        return {
            arrayOfTasks: [],
            showAddTask: false //we have a button based on the value of showAddTask
        }
    },
    methods: {
        toggleAddTask() {
            this.showAddTask = !this.showAddTask //if the method is called change the value of its opposite
        },
        addTask(newTask) {
            this.arrayOfTasks = [...this.arrayOfTasks, newTask]
        },

        deleteTask(id) {
            this.arrayOfTasks = this.arrayOfTasks.filter((task) => {
                return (task.id !== id)
            })
        },
        toggleReminder(id) {
            this.arrayOfTasks = this.arrayOfTasks.map((task) => task.id === id ? { ...task, reminder: !task.reminder } : task)
        }
    },
    created() {
        this.arrayOfTasks = [
            {
                id: 1,
                text: "Doctors Appointment",
                day: "March 1st ar 2:30om",
                reminder: true
            },
            {
                id: 2,
                text: "Meeting at school",
                day: "March 3rd at 1:30pm",
                reminder: true

            },
            {
                id: 3,
                text: "Food Shopping",
                day: "March 3rd at 11:00 am",
                reminder: false

            }
        ]
    }


}
</script>





<template>
    <div class="container">
        <Header @toggle-add-task="toggleAddTask" text="Task Tracker" :addTaskButtonState="showAddTask" />
        <div v-if="showAddTask">
            <!--condition directive v-if === div will only be rendered if the directives expression ("showAddTask") returns TRUE-->
            <AddTask @add-task="addTask" /> <!--on @add-task we want to call addTask method-->
        </div>
        <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="arrayOfTasks" />
    </div>
</template>





<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: 'Poppins', sans-serif;
}

.container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
}

.btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
}

.btn:focus {
    outline: none;
}

.btn:active {
    transform: scale(0.98);
}

.btn-block {
    display: block;
    width: 100%;
}
</style>

