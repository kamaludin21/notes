<template>
  <p class="font-medium text-lg dark:text-white">Task Form</p>
  <form @submit="onSubmit" action="" class="mb-2">
    <div class="flex flex-col w-full">
      <label for="text" class="font-medium text-sm leading-loose dark:text-white">Task</label>
      <input
        v-model="text"
        name="text"
        id="text"
        class="py-1.5 px-2 rounded border-2 border-purple-100 focus:outline-none focus:ring-1 focus:ring-purple-600 focus:border-transparent shadow-sm"
      />
    </div>
    <div class="flex flex-col w-full">
      <label for="day" class="font-medium text-sm leading-loose dark:text-white">Day</label>
      <input
        v-model="day"
        name="day"
        id="day"
        class="py-1.5 px-2 rounded border-2 border-purple-100 focus:outline-none focus:ring-1 focus:ring-purple-600 focus:border-transparent shadow-sm"
      />
    </div>
    <div class="flex flex-row w-full items-center justify-between mb-2">
      <label class="inline-flex items-center mt-3">
        <span class="mr-2 text-gray-700 dark:text-white">Reminder</span>
        <input
          v-model="reminder"
          name="reminder"
          type="checkbox"
          class="form-checkbox h-5 w-5 text-purple-600"
          checked
        />
      </label>
      <button
        type="submit"
        class="py-1 px-2 text-sm rounded focus:outline-none bg-blue-400 hover:bg-blue-600 hover:shadow-lg font-medium uppercase text-white select-none"
      >
        Submit
      </button>
    </div>
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: "",
      day: "",
      reminder: false,
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      if (!this.text) {
        alert("Task still empty");
        return;
      }

      const newTask = {
        // id: Math.floor(Math.random() * 1000),
        text: this.text,
        day: this.day,
        reminder: this.reminder,
      };
      this.$emit("add-task", newTask)((this.text = "")),
        (this.day = ""),
        (this.reminder = false);
    },
  },
  emits: ["add-task"],
};
</script>