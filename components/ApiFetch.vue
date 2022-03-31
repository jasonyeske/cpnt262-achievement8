<template>
    <p> {{ characters }} </p>
</template>

<script setup>
import { ref } from 'vue';

const characters = ref("");

async function fetchCharacters() {
  try {
    const res = await $fetch('https://api.disneyapi.dev/characters');
    if(res.ok) {
      throw new Error(`${res.status }`)
    }

    const data = await res;
    characters.value = await data.data


    console.log(data)
  } catch (err) {
    throw new Error('Async fetch error: ' + err)
  }
}
fetchCharacters();


</script>