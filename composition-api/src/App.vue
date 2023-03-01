<script setup>
import { ref, computed } from "vue";
const title = "Shopping List App";
const shoppingList = ref([]);
const newItem = ref("");
const showForm = ref(false);
const addNewitem = () => {
  // Add your code here
};

const numberOfItems = computed(() => {
  // Add your code here
});

const disable = computed(()=>{
 // Add our code here
})
</script>

<template>
  <div
    class="w-[50rem] bg-white py-6 px-4 rounded-md shadow-2xl text-black text-left flex flex-col gap-4"
  >
    <h1 class="text-3xl font-bold">{{ title }}</h1>
    <form @submit.prevent="addNewitem">
      <div class="flex flex-col gap-2" v-if="showForm">
        <input
          type="text"
          placeholder="Add a new item"
          class="px-4 py-2 text-gray-200"
          v-model="newItem"
          
        />
      </div>
      <div class="flex gap-2">
        <button
          :class="disable?'bg-gray-500 text-gray-400':'bg-green-500 hover:bg-green-600'"
          class="text-white font-bold mt-4"
          type="submit"
          @click="showForm = true"
          
        >
          Add New Item
        </button>
        <button
          class="bg-red-500 text-white font-bold mt-4 hover:bg-red-600"
          @click="showForm = false"
          v-if="showForm"
        >
          Close
        </button>
      </div>
    </form>
    <div
      class="bg-pink-100 p-2 flex gap-2 items-center"
      v-if="numberOfItems >= 5"
    >
      <i
        class="fa-sharp fa-solid fa-triangle-exclamation text-red-500 text-2xl"
      ></i>
      <p class="font-bold text-sm italic text-gray-600">
        You are over budget!!
      </p>
    </div>
    <div class="italic" v-if="shoppingList.length > 0">
      <p v-for="item in shoppingList" class="font-semibold">{{ item }}</p>
    </div>
    <div v-else>
      <p class="font-bold italic">No items in your list</p>
    </div>
  </div>
</template>

