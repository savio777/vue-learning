<script setup lang="ts">
import { computed, ref } from "vue";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faTrash, faPlusCircle } from "@fortawesome/free-solid-svg-icons";

const list = ref<{ name: string; age: number }[]>([]);

const isShowOnlyAdult = ref(false);

const name = ref("");
const age = ref<number | undefined>();

const addPerson = () => {
  if (name.value && age.value) {
    list.value.push({ name: name.value, age: age.value });
    name.value = "";
    age.value = undefined;
  }
};

const removePerson = (index: number) => {
  list.value.splice(index, 1);
};

const listFiltered = computed(() => {
  return isShowOnlyAdult.value
    ? list.value.filter((person) => person.age >= 18)
    : list.value;
});
</script>

<template>
  <div class="flex flex-col items-center justify-center p-6 gap-2">
    <h1 class="text-2xl font-bold">Pessoas {{ list.length }}</h1>

    <span class="text-gray-700">Adicionar Pessoa</span>

    <div class="flex items-center justify-center gap-2 mb-4">
      <input
        type="text"
        v-model="name"
        placeholder="Nome"
        class="p-2 border rounded"
      />
      <input
        type="number"
        v-model="age"
        placeholder="Idade"
        class="p-2 border rounded"
      />
      <button class="p-2 bg-blue-500 text-white rounded" @click="addPerson">
        <FontAwesomeIcon :icon="faPlusCircle" />
      </button>
    </div>

    <div>
      <input type="checkbox" v-model="isShowOnlyAdult" />
      <span class="ml-1 text-gray-700">Mostrar apenas adultos</span>
    </div>

    <ul
      v-if="list.length"
      class="flex flex-col gap-2 border rounded p-4 w-full max-w-md bg-gray-300"
    >
      <li
        v-for="(person, index) in listFiltered"
        :key="index"
        class="space-x-2 flex items-center justify-between p-1 border rounded bg-white border-gray-400"
      >
        <span>{{ person.name }} - {{ person.age }}</span>
        <button class="text-red-500" @click="removePerson(index)">
          <FontAwesomeIcon :icon="faTrash" />
        </button>
      </li>
    </ul>
  </div>
</template>
