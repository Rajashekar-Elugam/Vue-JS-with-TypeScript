<template>
  <div class="app">
    <!-- <Introduction /> -->
    <AppJob />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

// import Introduction from "./components/Introduction.vue";
import AppJob from "./components/AppJob.vue";

export default defineComponent({
  name: "App",
  components: {
    // Introduction,
    AppJob,
  },
});
</script>

<style scoped>
.app {
  background: lightseagreen;
}
</style>
