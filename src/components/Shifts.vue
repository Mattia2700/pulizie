<script setup lang="ts">
// TODO: better way to do this, like a object with place, color and text_color
const places = ["Bagno", "Cucina", "Pavimenti"];
const colors = ["bg-[#F25F5C]", "bg-[#FFE066]", "bg-[#247BA0]"];
const text_colors = ["text-white", "text-black", "text-white"];
</script>

<template>
  <div class="flex flex-col h-full">
    <h1
      v-for="(p, i) in places"
      class="flex-1 flex items-center justify-center text-2xl font-bold"
      :class="[colors[i], text_colors[i]]"
    >
      {{ p }}
    </h1>
  </div>
</template>

<style scoped></style>
