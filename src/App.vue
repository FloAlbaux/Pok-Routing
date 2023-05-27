<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <nav>    
    <a href="/">Home</a>
    <a href="/about">About</a>
  </nav>

  <main>
    <RouterView/>
  </main>
</template>

