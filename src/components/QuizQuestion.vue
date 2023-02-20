<template>
   <div>
      <p class="mt-8 text-2xl font-bold" v-text="question"></p>

      <div class="my-8 flex flex-col gap-3">

        <p class="bg-slate-400 text-white px-14 py-2 rounded-lg font-bold hover:bg-blue-500 cursor-pointer" v-for="option in options" :key="option" v-text="option"
        :class="userAnswer === option && 'bg-blue-500'"
        @click="submittedUserAnswer(option)"
        >

        </p>
        
      </div>

      <div class="text-center">
          <button :disabled="btnDisabled"  class="bg-green-400 px-8 py-2 rounded-xl hover:bg-green-600 disabled:opacity-70 disabled:cursor-not-allowed" 
        @click="nextQuestion"
          >
                {{ idQuestion + 1 != 4 ? 'Suivant' : 'Terminer'}}
        </button>
      </div>
    </div>
</template>

<script setup>
    const {idQuestion, question, options, btnDisabled, userAnswer, submittedUserAnswer, nextQuestion} = defineProps(['idQuestion', 'question', 'options', 'btnDisabled', 'userAnswer', 'submittedUserAnswer', 'nextQuestion']);
    
</script>

<style lang="scss" scoped>

</style>
