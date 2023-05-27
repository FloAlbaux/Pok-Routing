<script setup lang="ts">
import { ref } from 'vue'

const props = defineProps(['rarety'])
const emit = defineEmits(['pokemon-catched'])

let rarety = ref(props.rarety);

function handleClick() {
    let pokeball = document.getElementsByClassName("pokeball")[0];

    let pokeballButton = document.getElementsByClassName("pokeball-button-circle")[0];

    let stars = document.getElementsByClassName("stars")[0];

    pokeball.classList.add("pokeball-active");
    pokeballButton.classList.add("pokeball-middle-button-active");
    console.log(rarety)

    const randomNumber = Math.floor(Math.random() * 101); 
    if (randomNumber <= rarety.value) {
        console.log("yes")
        setTimeout(() => {
            emit("pokemon-catched");
        }, 4200);
    }
}

</script>

<template>
    <div>
        <div class="pokeball"  @click="handleClick">
            <div class="pokeball-top"></div>
            <div class="pokeball-middle"></div>
            <div class="pokeball-button">
                <div class="pokeball-button-circle"></div>
            </div>
            <div class="pokeball-bottom"></div>
        </div>
    </div>  
</template>

<style scoped>
    body {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 50px;
  background-color: #E1E1E1;
}

.pokeball {
  position: relative;
  width: 200px;
  overflow: hidden;
  transform-origin: bottom;
  cursor: pointer;
}

.pokeball-active {
  animation: catching 4s ease-in-out;
}

.pokeball-top {
  width: 200px;
  height: 100px;
  border-top-left-radius: 150px;
  border-top-right-radius: 150px;
  background-color: red;
}

.pokeball-bottom {
  width: 200px;
  height: 100px;
  border-bottom-left-radius: 100px;
  border-bottom-right-radius: 100px;
  background-color: white;
}

.pokeball-middle {
  width: 200px;
  height:24px;
  background-color: black;
  position: absolute;
  top: 88px;
}

.pokeball-middle-button-active {
  animation: light 4s ease-in-out;
}

.pokeball-button {
  height: 40px;
  width: 40px;
  background-color: white;
  border: 5px solid black;
  border-radius: 100%;
  position: absolute;
  top: 75px;
  left: 75px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.pokeball-button-circle {
  border: 1px solid black;
  height: 30px;
  width: 30px;
  border-radius: 30px;
}

@keyframes catching {
  10% { transform: rotate(20deg); }
  20% { transform: rotate(0deg); }
  30% { transform: rotate(0deg); }
  40% { transform: rotate(-20deg); }
  50% { transform: rotate(0deg); }
  60% { transform: rotate(0deg); }
  70% { transform: rotate(10deg); }
  80% { transform: rotate(0deg); }
  100% { transform: rotate(0deg); }
}

@keyframes light {
  10% { 
    background-color: #fde295;
    box-shadow: -5px -5px 15px 2px rgba(255,248,88,0.5);
    box-shadow: 5px 5px 15px 2px rgba(255,248,88,0.5);
  }
  20% { background-color: white; }
  30% { background-color: white; }
  40% { background-color: #fde295;
    box-shadow: -5px -5px 15px 2px rgba(255,248,88,0.5);
    box-shadow: 5px 5px 15px 2px rgba(255,248,88,0.5); }
  50% { background-color: white; }
  60% { background-color: white; }
  70% { background-color: #fde295;
    box-shadow: -5px -5px 15px 2px rgba(255,248,88,0.5);
    box-shadow: 5px 5px 15px 2px rgba(255,248,88,0.5); }
  80% { background-color: white; }
  100% { background-color: white; }
}

button {
  margin-bottom: 30px;
  padding: 5px 15px;
  border-radius: 0;
  border: 1px solid #333;
  cursor: pointer;
}
</style>