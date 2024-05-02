<template>
  <div class="flex flex-col">
    <h1 class="text-center text-3xl font-bold">Cat breeds</h1>
    <div class="p-2">
      <ul class="grid grid-cols-4 gap-2">
        <!-- {{ pending? "loading...": breeds }} -->
        <li v-for="breed in breeds" :key="breed.id" class="h-28 w-28">
          <!-- {{ breed.url }} -->
          <img
            :src="`${breed.url}`"
            v-bind:alt="picture"
            class="w-full h-full"
          />
        </li>
      </ul>
    </div>
    <button class="bg-slate-600 text-white p-2 m-auto rounded text-2xl border border-black items-center hover:bg-slate-400 uppercase" @click="refresh">
        refresh
    </button>
    <a href="http://www.github.com/manuelbamise" target="_blank" class="m-auto">Manuel</a>
  </div>
</template>

<script lang="ts" setup>
import {ref} from 'vue';

const { data: breeds, pending } = await useFetch(
  "http://localhost:4444/getdata"
);
//  console.log(breeds.value);

const refresh=()=>{
    window.location.reload();
}
</script>
