<script setup>
import { RouterLink } from 'vue-router';
const { result, quizLength } = defineProps(['result', 'quizLength'])

</script>


<template>
    <div class="result">
        <p>Your Results...</p>
        <h1>{{ result }}/{{ quizLength }} </h1>
    </div>
    <RouterLink to="/">Go Back</RouterLink>
</template>


<style scoped>
.result {
    text-align: center;
    margin-top: 20px;
    padding: 100px 0;
}

p {
    font-size: 25px;
}

h1 {
    font-size: 50px;
}
</style>