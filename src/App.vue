<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
      <nav class="flex items-center gap-5 justify-center text-[35px]">
        <RouterLink to="/" class="text-blue-400 hover:text-red-400">Home</RouterLink>
        <RouterLink  to="/quiz" class="text-blue-400 hover:text-red-400">Quiz</RouterLink>
      </nav>
  </header>

  <RouterView />
</template>

<style scoped>
  
</style>
