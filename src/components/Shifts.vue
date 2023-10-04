<script setup lang="ts">
// TODO: better way to do this, like a object with place, color and text_color
import { onMounted, ref, watch } from "vue";

const places = ["Bagno", "Cucina", "Pavimenti"];
const colors = ["bg-[#F25F5C]", "bg-[#FFE066]", "bg-[#247BA0]"];
const text_colors = ["text-white", "text-black", "text-white"];

const people = ["Mattia", "Fafa", "Arbjo", "Peppe", "Gabri"];
const indeces = [0, 0, 1];

const new_order = ref([...people]);

const props = defineProps({
  week: Number,
});

watch(
  () => props.week,
  () => {
    computeShift();
  },
);

onMounted(() => {
  computeShift();
});

function computeShift() {
  const shifts = props.week! % people.length;
  // compute shift without modifying the original array
  new_order.value = [...people];
  new_order.value = new_order.value
    .slice(shifts)
    .concat(new_order.value.slice(0, shifts));
}

function nextPerson(current: string) {
  const index = people.indexOf(current);
  return people[(index + 1) % people.length];
}
</script>

<template>
  <div class="flex flex-col h-[100svh] md:h-screen justify-between">
    <div
      v-for="(p, i) in places"
      class="flex-1 flex"
      :class="[colors[i], text_colors[i]]"
    >
      <div class="hidden md:block w-1/3" />
      <div class="flex flex-col w-full items-center">
        <div class="flex flex-1 flex-col justify-center items-center">
          <p class="text-3xl font-bold">{{ p }}</p>
          <p class="mt-4 text-2xl">{{ new_order[i + indeces[i]] }}</p>
        </div>
        <p class="flex md:hidden mb-2 whitespace-nowrap">
          <b>Prossimo:</b> &nbsp; {{ nextPerson(new_order[i + indeces[i]]) }}
        </p>
      </div>
      <div class="hidden md:flex items-end justify-end w-1/3">
        <p class="pr-4 pb-2 whitespace-nowrap text-xl">
          <b>Prossimo:</b> &nbsp; {{ nextPerson(new_order[i + indeces[i]]) }}
        </p>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
