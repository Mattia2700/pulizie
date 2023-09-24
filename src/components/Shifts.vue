<script setup lang="ts">
import { ref } from 'vue'

const places = ["Bagno", "Cucina", "Pavimenti"]

</script>

<template>
  <div class="flex flex-col h-full">
    <h1 v-for="p in places" class="flex-1 flex items-center justify-center text-2xl">{{p}}</h1>
  </div>
</template>

<style scoped>

</style>
