<script setup>
import { ref } from "vue"
  const items = ref(["Eggs","Tomatoes","Avocado"])
  const completed = ref([])
</script>

<template>
  <div class="flex flex-col p-4 rounded-md bg-white gap-2">
     <header class="flex justify-between">
        <h2>Groceries</h2>
     </header>
     <div class="flex flex-col">
           <ul>
            <li v-for="item in items">{{ item }}</li>
           </ul> 
        </div>
  </div>
</template>