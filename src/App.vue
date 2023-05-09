<script setup>
import Card from "./components/Card.vue";

import q from "./data/quizes.json"
import { ref, watch } from "vue"


const quizes = ref(q)
const search = ref("")


watch(search, () => {
  quizes.value = q.filter(q => q.name.toLowerCase().includes(search.value.toLowerCase()))
})
</script>


<template>
  <div class="container">
    <header>
      <h1>Quizes</h1>
      <input v-model.trim="search" type="text" placeholder="Search..." />
    </header>
    <div class="cards-container">
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
    </div>
  </div>
</template>


<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

header {
  margin-top: 30px;
  margin-bottom: 15px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 10px;
}

header input {
  border: none;
  background: rgba(128, 128, 128, 0.1);
  padding: 10px;
}

.cards-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
  gap: 20px;
}
</style>

