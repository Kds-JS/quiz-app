<template>
<div>
  <div v-if="quizLevel != 2">

    <div>
        <div v-if="score >= 2" class="flex items-center justify-between flex-wrap gap-5 mt-8">
            <h1>Bravo, vous passez au niveau suivant</h1>
            <button class="bg-green-400 px-8 py-2 rounded-xl hover:bg-green-600"
            @click="nextLevel"
            >
                Niveau Suivant
            </button>
        </div>

        <p v-else class="text-orange-400 text-center my-12">
            Echoué, vous serez redirigez vers le niveau précedent dans 5 secondes.....
        </p>
    </div>


    <div class="flex items-center justify-between flex-wrap gap-5 my-8 font-bold">
      <div class="py-4 px-10 bg-slate-700 rounded-2xl">Score: {{(score / 4) *100}}%</div>

      <div class="py-4 px-10 bg-slate-700 rounded-2xl">Note: {{ score }} / 4</div>
    </div>
  </div>

  <div v-else class="text-center">
        <p class="text-4xl text-green-700 my-12">Félicitations, Vous aviez terminé le Quiz 🎉🎉🎉</p>
        <button @click="restartQuiz" class="bg-green-400 px-8 py-2 rounded-xl hover:bg-green-600">Reprenez le Quiz</button>
  </div>
</div>
</template>

<script setup>
    import {ref, watchEffect} from 'vue';

     const {score, quizLevel, nextLevel, restartLevel, restartQuiz} = defineProps(['score', 'quizLevel', 'nextLevel', 'restartLevel', 'restartQuiz']);

     watchEffect(() => {
       if(score < 2 ){
            setTimeout(() => {
                restartLevel();
            }, 5000);
       }
     })
</script>

<style scoped>

</style>
