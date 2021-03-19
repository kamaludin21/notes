<template>
  <header class="flex flex-row justify-between items-center">
    <h1 class="text-2xl uppercase font-black font-medium">
      <span
        class="bg-clip-text text-transparent bg-gradient-to-r from-blue-400 to-purple-500"
      >
        {{ title }}
      </span>
    </h1>
    <Button
      v-show="homePage"
      @toggle-add-task="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'Add Task'"
      :color="
        showAddTask
          ? 'bg-red-400 hover:bg-red-600'
          : 'bg-purple-400 hover:bg-purple-600'
      "
    />
  </header>
</template>

<script>
import Button from "./Button";

export default {
  name: "Header",
  props: {
    title: {
      type: String,
      default: "Title",
    },
    showAddTask: Boolean,
  },
  components: {
    Button,
  },
  computed: {
    homePage() {
      if (this.$route.path === "/") {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>
