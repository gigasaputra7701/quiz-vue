<script setup>
import { ref, watch } from "vue";
import srcQuiz from "../data/quizes.json";
import QuizCard from "../components/QuizCard.vue";

const search = ref("");
const quizes = ref(srcQuiz);

watch(search, () => {
  quizes.value = srcQuiz.filter((quiz) => {
    return quiz.title.toLowerCase().includes(search.value.toLocaleLowerCase());
  });
});
</script>

<template>
  <header>
    <h1 id="title">Quiz App</h1>
    <input
      v-model.trim="search"
      type="text"
      id="search-box"
      placeholder="Search Quiz.."
    />
  </header>
  <section id="quiz-container">
    <QuizCard v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
  </section>
</template>

<style scoped>
header {
  margin: 30px 0px;
  display: flex;
  justify-content: space-evenly;
  align-items: center;
}
#title {
  font-size: 32px;
  font-weight: bold;
}
#search-box {
  padding: 12px 18px;
  background-color: #c9c9c9;
  border: none;
  border-radius: 5px;
}
#quiz-container {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  padding: 0px 40px;
  margin-top: 20px;
  gap: 30px;
}
</style>
