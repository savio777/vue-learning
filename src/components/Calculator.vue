<script setup lang="ts">
import { onMounted, onUnmounted, ref, watch, watchEffect } from "vue";
const count = ref(0);

// useEffect style
onMounted(() => {
  console.log(`Hello :)`);
});
onUnmounted(() => {
  console.log(`Goodbye :)`);
});

// useEffect with automatic dependencies
watchEffect(() => {
  console.log(count.value);
});

// useEffect with dependencies
watch(count, (newValue) => {
  console.log(`Count changed to: ${newValue}`);
});
</script>

<template>
  <div class="flex flex-col gap-2 items-center justify-center">
    <h1 v-if="count > 0" class="text-2xl font-bold">Counter: {{ count }}</h1>
    <input type="number" v-model="count" class="p-2 border rounded" />
    <button class="p-2 bg-blue-500 text-white rounded" @click="count++">
      Increment
    </button>
  </div>
</template>
