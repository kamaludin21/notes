<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="task.reminder ? 'border-l-4 pl-4' : 'pl-5'" class="mb-2 flex flex-row m-full justify-between bg-gray-200 border-purple-400 items-center hover:shadow-md select-none" >
    <div class="my-2 select-none">
      <p class="text-base font-medium leading-none">{{ task.text }}</p>
      <p class="text-sm font-base">{{ task.day }}</p>
      <p class="text-xs font-light leading-loose">Reminder: {{ task.reminder ? 'ON' : 'OFF' }}</p>
    </div>
    <div @click="$emit('delete-task', task.id)" class="p-5">   
      <svg

        class="h-5 w-5 fill-current text-gray-400 hover:text-red-600"
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M6 18L18 6M6 6l12 12"
        />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object,
  },
  emits: ['delete-task', 'toggle-reminder']
};
</script>