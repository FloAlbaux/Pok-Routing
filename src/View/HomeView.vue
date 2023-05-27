<script setup lang="ts">
import { ref, onBeforeMount } from 'vue'

let data = ref([]);

onBeforeMount(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=100")
    .then(response => response.json())
    .then(output => (data.value = output.results));
})

</script>


<template>
    <ul class="list">
      <li class="poke-box" v-for="pokemon in data" :key="pokemon.url">{{ pokemon.name }}</li>
    </ul>
</template>

<style scoped>
  /* Appliquer un style aux éléments de liste */
  .list {
    display: flex;
    flex-wrap: wrap;
    list-style: none;
    padding: 0;
  }

  /* Appliquer un style aux éléments de liste imbriqués */
  .poke-box {
    box-sizing: border-box;
    width: 20%; /* Pour afficher au maximum 5 boîtes par ligne */
    padding: 10px;
    margin: 10px;
    box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3); /* Ajouter une ombre */
    border-radius: 5px; /* Arrondir les bords */
    background-color: #F0F0F0; /* Ajouter de la couleur de fond */
  }

</style>
