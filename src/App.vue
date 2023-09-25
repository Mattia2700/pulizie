<script setup lang="ts">
import Shifts from "./components/Shifts.vue";
import TopBar from "./components/TopBar.vue";
import { ref } from "vue";

// get current week number
const currentDate = new Date();
const startDate = new Date(currentDate.getFullYear(), 0, 1);
const days = Math.floor(
  (currentDate.valueOf() - startDate.valueOf()) / (24 * 60 * 60 * 1000),
);
const weekNumber = ref(Math.ceil(days / 7));
</script>

<template>
  <div class="flex flex-col h-screen">
    <TopBar
      :week="weekNumber"
      @prev-week="weekNumber--"
      @next-week="weekNumber++"
    />
    <Shifts :week="weekNumber" />
  </div>
</template>

<style scoped>
@supports (-webkit-touch-callout: none) {
  .h-screen {
    height: -webkit-fill-available;
  }
}
</style>
