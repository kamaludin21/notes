<template>
  <div id="app" class="m-2 lg:mx-auto md:w-2/5 bg-gray-100 shadow-lg">
    <div class="py-2 flex flex-col px-4 rounded-md border-2 border-purple-800">
      <Header
        @toggle-add-task="toggleAddTask"
        :showAddTask="showAddTask"
        title="Task Notes"
      />
      <hr
        class="h-0.5 bg-black my-2 bg-gradient-to-r from-blue-800 to-purple-500"
      />
      <div v-show="showAddTask">
        <AddTask @add-task="addTask" />
      </div>
      <Tasks
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask"
        :tasks="tasks"
      />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: {
    Header,
    AddTask,
    Tasks,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Confirm delete?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
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
        text: "Follow a github",
        day: "June 21th at 19:00",
        reminder: true,
      },
      {
        id: 2,
        text: "Killing spike for a moment",
        day: "June 21th at 19:00",
        reminder: true,
      },
      {
        id: 3,
        text: "Memories are gone",
        day: "June 21th at 19:00",
        reminder: false,
      },
    ];
  },
};
</script>


<style>
@import "./assets/styles.css";
</style>
