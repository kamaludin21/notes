<template> 
  <p class="font-medium text-lg mb-2 dark:text-white">Task list</p>
  <div
    @toggle-reminder="$emit('toggle-reminder', task.id)"
    :key="task.id"
    v-for="task in tasks"
  >
    <Task
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>