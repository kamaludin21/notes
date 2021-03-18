<template>
  <button
    @click="$emit('toggle-add-task')"
    :class="color"
    class="py-2 px-4 rounded focus:outline-none hover:shadow-lg font-medium uppercase text-white select-none">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: "Action button",
    },
    color: String,
    showAddTask: Boolean
  },
  
};
</script>