<template>
  <div class="home">
    <button>click me</button>
  </div>
</template>

<script setup>
import { ref,  onMounted } from "vue";

const pokemonsDeMierda = ref([]);

const fetchPokemon = () => {
  fetch('https://pokeapi.co/api/v2/pokemon?offset=0')
    .then((res)=> res.json())
    .then((data) => {
      pokemonsDeMierda.value = data.results
      console.log(pokemonsDeMierda.value)
    })
}

onMounted(() => {
  fetchPokemon()
})
</script>
