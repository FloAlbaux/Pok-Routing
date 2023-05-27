<script setup lang="ts">
import { RouterView, RouterLink } from 'vue-router'
</script>

<template>
  <nav class="nav-bar">    
    <RouterLink to="/" active-class="active-link">Home</RouterLink>
    <RouterLink to="/about" active-class="active-link">About</RouterLink>
  </nav>

  <main>
    <RouterView/>
  </main>
</template>

<style scoped>
  /* Appliquer un style à la navigation */
  .nav-bar {
    position: sticky;
    top: 0;
    background-color: #f5f5f5;
    padding: 10px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 100;
  }

  /* Appliquer un style aux liens de navigation */
  .nav-bar a {
    margin-right: 10px;
    color: #333;
    text-decoration: none;
    font-weight: bold;
    transition: color 0.3s ease-in-out;
  }

  /* Appliquer un style au lien actif */
  .active-link {
    color: #ff0000;
  }
</style>
