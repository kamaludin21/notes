<template>
  <div
    id="app"
    class="m-2 lg:mx-auto md:w-2/5 bg-gray-100 dark:bg-gray-700 rounded-md shadow-lg"
  >
    <div class="py-2 flex flex-col px-4 rounded-md border-2 border-purple-800">
      <Header
        @toggle-add-task="toggleAddTask"
        :showAddTask="showAddTask"
        title="Task Notes"
      />
      <hr
        class="h-0.5 bg-black my-2 bg-gradient-to-r from-blue-800 to-purple-500"
      />
      <router-view :showAddTask="showAddTask"></router-view>
      <Footer />
      <div class="">
        <div
          class="relative inline-block w-10 mr-2 align-middle select-none transition duration-200 ease-in"
        >
          <input
            @click="switchToggle()"
            type="checkbox"
            name="toggle"
            id="toggle"
            class="toggle-checkbox absolute block w-6 h-6 focus:select-none rounded-full bg-white border-4 appearance-none cursor-pointer"
            v-model="darkModeStatus"
          />
          <label
            for="toggle"
            class="toggle-label block overflow-hidden h-6 rounded-full bg-gray-300 cursor-pointer"
          ></label>
        </div>
        <label for="toggle" class="text-xs text-purple-800 dark:text-white">{{ darkMode ? 'Dark' : 'Light' }} mode</label>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Footer from "./components/Footer";

export default {
  name: "App",
  components: {
    Header,
    Footer,
  },
  data() {
    return {
      darkMode: Boolean,
      showAddTask: false,
    };
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    dark() {
      localStorage.setItem("theme", "dark");
      document.querySelector('html').classList.add('dark')
      document.getElementById("toggle").checked = true;
      this.darkMode = true
    },
    light() {
      localStorage.setItem("theme", "light");
      document.querySelector('html').classList.remove('dark')
      document.getElementById("toggle").checked = false
      this.darkMode = false
    },
    switchToggle() {
      if(this.darkMode || document.querySelector('html').classList.add('dark')) {
        this.light() 
      } else {
        this.dark()
      }
    },  
    
  },
  computed: {
    darkModeStatus() {
      return (localStorage.theme === 'dark' ? true : false)
    }
  }
};
</script>

<style>
@import "./assets/styles.css";
</style>

<style scoped lang="postcss">
.toggle-checkbox:checked {
  @apply: right-0 border-green-400;
  right: 0;
  border-color: #68d391;
}
.toggle-checkbox:checked + .toggle-label {
  @apply: bg-green-400;
  background-color: #68d391;
}
</style>
