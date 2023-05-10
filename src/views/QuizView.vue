<script setup>
import { useRoute } from "vue-router"
import { ref, computed } from "vue";


import QuizHeader from "../components/QuizHeader.vue"
import Question from "../components/Question.vue"
import Result from "../components/Result.vue"

import q from "../data/quizes.json"

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = q.find(quiz => quiz.id === quizId)

const currentQuestionIndex = ref(0)
const correctAnswers = ref(0)
const showResults = ref(false)


const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barPercentage = computed(() => currentQuestionIndex.value / quiz.questions.length * 100 + '%')





const onOptionSelected = (isCorrect) => {
    if (isCorrect) {
        correctAnswers.value++
    }
    if (quiz.questions.length - 1 === currentQuestionIndex.value) {
        showResults.value = true
    }

    currentQuestionIndex.value++
}

</script>

<template>
    <div>
        <div class="container">
            <QuizHeader :questionStatus="questionStatus" :barPercentage="barPercentage" />
            <div class="question-container">
                <Question v-if="!showResults" :question="quiz.questions[currentQuestionIndex]"
                    @selectOption="onOptionSelected" />
                <Result v-else :result="correctAnswers" :quizLength="quiz.questions.length" />
            </div>
        </div>
    </div>
</template>