<script setup>
import { useRouter } from 'vue-router'


const router = useRouter()
const { quiz } = defineProps(['quiz'])

const navigateToQuiz = () => {
    router.push(`/quiz/${quiz.id}`)
}
</script>

<template>
    <div class="card" @click="navigateToQuiz">
        <img :src="quiz.img" alt="Quiz Image">
        <div class="card-text">
            <h2>{{ quiz.name }}</h2>
            <p>{{ quiz.questions.length }}</p>
        </div>
    </div>
</template>


<style scoped>
.card {
    width: 310px;
    overflow: hidden;
    border-radius: 4px;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 10px;
}

.card img {
    width: 100%;
    height: 190px;
    margin: 0;
}

.card-text {
    padding: 0 5px;
}

.card h2 {
    font-weight: bold;
}
</style>