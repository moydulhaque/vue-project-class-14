<script setup>
import {RouterLink, RouterView} from 'vue-router'
</script>

<template>

  <nav class="p-4 mb-4">
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
  </nav>
  <hr>

  <RouterView/>
</template>

<style scoped>

</style>
