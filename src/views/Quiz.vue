<template>
  <div >

    <div v-if="!quizEnd">
      <Levels :levelNames="levelNames" :quizLevel="quizLevel"/>
      <ProgressBar :idQuestion="idQuestion" :maxQuestion="maxQuestion"/>
      <QuizQuestion 
      :idQuestion="idQuestion"
      :question="question" 
      :options="options" 
      :btnDisabled="btnDisabled"
      :userAnswer="userAnswer"
      :submittedUserAnswer="submittedUserAnswer" :nextQuestion="nextQuestion"/>
    </div>
    
    <div v-else>
      <QuizOver :score="score" :quizLevel="quizLevel" :nextLevel="nextLevel" :restartLevel="restartLevel" :restartQuiz="restartQuiz"/>
    </div>
  </div>
</template>

<script setup>
  import { quizData } from '../../data/quizData';
  import Levels from '../components/Levels.vue';
  import ProgressBar from '../components/ProgressBar.vue';
  import QuizQuestion from '../components/QuizQuestion.vue';
  import QuizOver from '../components/QuizOver.vue';
  import {ref, watch, watchEffect} from 'vue';

  const quizEnd = ref(false);
  const levelNames = ref(['debutant','amateur','expert']);
  const quizLevel = ref(0);
  const storedQuestion = ref([]);
  const idQuestion = ref(0);
  const options = ref([]);
  const question = ref('');
  const maxQuestion = ref(4);
  const userAnswer = ref('');
  const progress = ref(true);
  const score = ref(0);
  const btnDisabled = ref(true);

  watchEffect(() => {
    const level = levelNames.value[quizLevel.value];
    storedQuestion.value = quizData[level];
    // console.log(storedQuestion);
  })

  watchEffect(() => {
      question.value = storedQuestion.value[idQuestion.value].quiz;
      options.value = storedQuestion.value[idQuestion.value].options;
      // console.log(options.value);
  })

  const submittedUserAnswer = submitAnswer => {
        userAnswer.value = submitAnswer;
        btnDisabled.value = false;       
    }

  const nextQuestion = () => {
    if(userAnswer.value === storedQuestion.value[idQuestion.value].answer) {
      score.value++;
    }

    if (idQuestion.value + 1 != maxQuestion.value) {
        idQuestion.value++;
        btnDisabled.value = true;
    } else {
        quizEnd.value = true;
    }
    
  }

  const nextLevel = () => {
    quizEnd.value = false;
    idQuestion.value = 0;
    score.value = 0;
    if(quizLevel.value != 2) {
      quizLevel.value++;
    } else {
      quizLevel.value = 0;
    }
  }

  const restartLevel = () => {
    quizEnd.value = false;
    idQuestion.value = 0;
    score.value = 0;
  }

  const restartQuiz = () => {
    quizEnd.value = false;
    idQuestion.value = 0;
    score.value = 0;
    quizLevel.value = 0;
  }
  
</script>

<style scoped>
  
</style>
