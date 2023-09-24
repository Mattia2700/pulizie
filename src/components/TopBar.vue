<script setup lang="ts">
// get current week number
const currentDate = new Date();
const startDate = new Date(currentDate.getFullYear(), 0, 1);
const days = Math.floor(
  (currentDate.valueOf() - startDate.valueOf()) / (24 * 60 * 60 * 1000),
);
const weekNumber = Math.ceil(days / 7);
</script>

<template>
  <div class="flex flex-col items-center justify-center bg-[#50514F]">
    <h1 class="text-white pt-4 text-4xl font-bold">Turni pulizie</h1>
    <h2 class="text-white py-2 text-2xl">Settimana {{ weekNumber }}</h2>
  </div>
</template>

<style scoped></style>
