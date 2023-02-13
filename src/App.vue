<template>
  <div class="container">
    <HeaderComponent @toggle-add-task="toggleAddTask" title="Task Tracker" />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <TasksCp
      @delete-task="deleteTask"
      :tasks="tasks"
      @toggle-reminder="toggleReminder"
    />
  </div>
</template>

<script>
import HeaderComponent from "./components/Header.vue";
import TasksCp from "./components/Tasks.vue";
import { defineComponent } from "vue";
import AddTask from "./components/AddTask.vue";
export default defineComponent({
  name: "App",
  components: {
    HeaderComponent,
    TasksCp,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    deleteTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctors Appointment",
        day: "March 1st at 1:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Meeting at school",
        day: "March 2nd at 1:30pm",
        reminder: true,
      },
      {
        id: 3,
        text: "Footbal match",
        day: "March 3rd at 20:00pm",
        reminder: false,
      },
    ];
  },
});
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
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
