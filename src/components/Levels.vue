<template>
  <div class="flex items-center flex-wrap gap-5 mt-6">
    <h1>Niveau :</h1>
    <h1 class="text-red-600" v-text="levelNames[quizLevel]"></h1>
  </div>
</template>

<script setup>
    const {levelNames, quizLevel} = defineProps(['levelNames', 'quizLevel']);
</script>

<style scoped></style>
