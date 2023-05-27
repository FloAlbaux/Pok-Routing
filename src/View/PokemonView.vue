<script setup lang="ts">
import { ref, onBeforeMount } from 'vue'
import { useRoute } from 'vue-router'
import Pokeball from '../components/PokeBall.vue'

const pokemon = ref({});
const isCatched = ref(false);
const route = useRoute();

function hasBeenCatched() {
    isCatched.value=true;
}

onBeforeMount(() => {
    const name = route.params.id;

    fetch(`https://pokeapi.co/api/v2/pokemon/${name}`)
        .then(response => response.json())
        .then(output => (pokemon.value = output));
    
})

</script>

<template>
    <h1>
        Beau {{ pokemon.name }} ! 
    </h1>
    <div class="detail">
        <div class="info">
            <p>Type : {{ pokemon.types[0].type.name }}</p>
            <p>Height : {{ pokemon.height }}</p>
        </div>
        <img :src="pokemon.sprites.back_default"/>
        <Pokeball @pokemon-catched="hasBeenCatched" :rarety="Math.floor(Math.random() * 101)"></Pokeball>
    </div>
    <h2 v-if="isCatched">Attrapé !!</h2>

    
</template>

<style scoped>
  .detail {
    display: flex;
    align-items: center;
    justify-content: space-around;
    background-color: #f5f5f5;
    padding: 10px;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }

  .info {
    margin-right: 20px;
  }

  h1 {
    font-size: 24px;
    color: #333;
    text-align: center;
    margin-bottom: 10px;
  }

  p {
    font-size: 16px;
    color: #666;
    margin-bottom: 5px;
  }

  img {
    max-width: 100%;
    height: auto;
    box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);
    border-radius: 5px;
  }
</style>