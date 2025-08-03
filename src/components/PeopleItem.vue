<script setup lang="ts">
import { defineProps } from "vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faTrash } from "@fortawesome/free-solid-svg-icons";

const { onRemove, person } = defineProps<{
  person: { name: string; age: number };
  onRemove: () => void;
}>();
</script>

<template>
  <li
    class="space-x-2 flex items-center justify-between p-1 border rounded bg-white border-gray-400"
  >
    <span>{{ person.name }} - {{ person.age }}</span>
    <button class="text-red-500" @click="onRemove">
      <FontAwesomeIcon :icon="faTrash" />
    </button>
  </li>
</template>
