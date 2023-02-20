<template>
  <div >
    <Levels/>
    <ProgressBar/>
  </div>
</template>

<script setup>
  import { quizData } from '../../data/quizData';
  import Levels from '../components/Levels.vue';
  import ProgressBar from '../components/ProgressBar.vue';
  import {ref} from 'vue';

  const quizEnd = ref(false);
  const levelNames = ref(['debutant','amateur','expert']);
  const quizLevel = ref(0);
  const storedQuestion = ref([]);
  const idQuestion = ref(0);
  const question = ref('');
  const maxQuestion = ref(4);
  const userAnswer = ref('');
  const progress = ref(true);
  const score = ref('');
  
</script>

<style scoped>
  
</style>
