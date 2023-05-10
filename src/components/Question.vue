<script setup>

const emit = defineEmits(['selectOption'])
const { question } = defineProps(['question'])


const emitSelectedOption = (isCorrect) => {
    emit('selectOption', isCorrect)
}
</script>


<template>
    <div class="question-container">
        <h1 class="question">{{ question.text }}</h1>
    </div>
    <div v-for="(option, index) in question.options" :key="index" class="options-container"
        @click="emitSelectedOption(option.isCorrect)">
        <div class="option">
            <p class="option-label">{{ option.label }}</p>
            <div class="option-value">{{ option.text }}</div>
        </div>
    </div>
</template>

<style scoped>
.question-container {
    margin-top: 25px;

}

.question {
    margin-bottom: 17px;
    border-radius: 3px 0 0 3px;
    font-size: 35px;
    padding: 10px 40px;
    background-image: linear-gradient(to right, rgb(0, 183, 255), rgba(0, 0, 0, 0));
    text-shadow: 1px 1px 3px brown;
}

.option {
    display: flex;
    margin-bottom: 20px;
    cursor: pointer;
    outline: 1px solid black;
    background-image: linear-gradient(to right, rgb(0, 140, 255), rgb(255, 255, 255));
    border-radius: 10px 0 0 10px;
}

.option:hover {
    outline: 3px solid rgb(180, 180, 180);
}

.option-label {
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    padding: 10px;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 10px;
    border-radius: 7px 0 0 7px;
}

.option-value {
    background-color: rgba(0, 0, 0, 0.5);
    width: 100%;
    font-size: 30px;
    padding-left: 10px;
}
</style>