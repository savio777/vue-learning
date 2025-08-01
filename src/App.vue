<script setup lang="ts">
import HelloWorld from "./components/HelloWorld.vue";
import Calculator from "./components/Calculator.vue";
import People from "./components/People.vue";
</script>

<template>
  <div class="flex flex-col h-screen w-full gap-10 bg-gray-50">
    <HelloWorld msg="Vite + Vue" />
    <Calculator />
    <People />
  </div>
</template>
