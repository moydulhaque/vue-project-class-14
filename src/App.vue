<script setup>
import {RouterLink, RouterView} from 'vue-router'
</script>

<template>

  <nav>
    <ul class="flex">
      <li class="p-2"> <RouterLink to="/">Home</RouterLink></li>
      <li class="p-2"><RouterLink to="/about">About</RouterLink></li>
    </ul>    
  </nav>
  <hr>

  <RouterView/>
</template>

<style scoped>

</style>
