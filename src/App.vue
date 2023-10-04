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

function decreaseWeek() {
  weekNumber.value--;
  if (weekNumber.value < 1) {
    weekNumber.value = 1;
  }
}
</script>

<template>
  <div class="flex flex-col h-[100svh]">
    <TopBar
      :week="weekNumber"
      @prev-week="decreaseWeek"
      @next-week="weekNumber++"
    />
    <Shifts :week="weekNumber" />
  </div>
</template>

<style scoped></style>
