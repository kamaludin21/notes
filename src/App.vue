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
      <router-view :showAddTask="showAddTask"></router-view>
      <Footer />
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
      showAddTask: false,
    };
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
  },
};
</script>


<style>
@import "./assets/styles.css";
</style>
