<template>
  <div>
    <h1>Pokémon List</h1>
    <ul>
      <!-- Iterate over pokemons array and display each pokemon's name and ID -->
      <li v-for="(pokemon, index) in pokemonsDeMierda" :key="index">
        {{ pokemon.name }}
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref,  onMounted } from "vue";

const pokemonsDeMierda = ref([]);
const urlIdPokemon = ref({})

const fetchPokemon = () => {
  fetch('https://pokeapi.co/api/v2/pokemon?offset=0')
    .then((res)=> res.json())
    .then((data) => {
      pokemonsDeMierda.value = data.results;
      data.results.forEach((pokemonsDeMierda, index) => {
        urlIdPokemon.value[pokemonsDeMierda.name] = index + 1; // Store the index as ID, add 1 to start from 1
      });
      console.log(pokemonsDeMierda.value);
      console.log(urlIdPokemon.value);
   });
}

onMounted(() => {
  fetchPokemon()
})
</script>
