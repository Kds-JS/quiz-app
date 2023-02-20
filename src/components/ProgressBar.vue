<template>
    <div>
        <div class="flex items-center justify-between flex-wrap gap-5 my-8 font-bold">
            <div class="py-4 px-10 bg-slate-700 rounded-2xl">
                Question: {{ idQuestion + 1 }}/4
            </div>

            <div class="py-4 px-10 bg-slate-700 rounded-2xl">
                Progression: {{ (idQuestion + 1) / maxQuestion * 100 }} %
            </div>

        </div>

        <div class="bg-gray-300 p-1 rounded-md">
            <div class="bg-red-700 text-white rounded-md text-center font-bold" :style="{ width: ((idQuestion + 1) / maxQuestion * 100) + '%'}">
                {{ (idQuestion + 1) / maxQuestion * 100 }}%
            </div>
        </div>
    </div>
</template>

<script setup>
    const {idQuestion, maxQuestion} = defineProps(['idQuestion', 'maxQuestion']);
</script>

<style scoped>

</style>