<script setup lang="ts">
import { IconChevronsLeft, IconChevronsRight } from "@tabler/icons-vue";

const props = defineProps({
  week: Number,
});

const emit = defineEmits<{
  (event: "nextWeek"): void;
  (event: "prevWeek"): void;
}>();
</script>

<template>
  <div class="flex flex-col items-center justify-center bg-[#50514F]">
    <h1 class="text-white pt-4 text-4xl font-bold">Turni pulizie</h1>
    <span class="flex items-center">
      <IconChevronsLeft class="text-white mr-3" @click="emit('prevWeek')" />
      <h2 class="select-none text-white py-4 text-2xl">
        Settimana {{ props.week }}
      </h2>
      <IconChevronsRight class="text-white ml-3" @click="emit('nextWeek')" />
    </span>
  </div>
</template>

<style scoped></style>
