<script setup>
import QuizContent from "@/components/QuizContent.vue";
import QuizHeader from "@/components/Header.vue";
import QuizResult from "@/components/QuizResult.vue";
import { useRoute } from "vue-router";
import quizes from "../data/quizes.json";
import { ref, computed } from "vue";

const route = useRoute();
const quizId = parseInt(route.params.id);
const quiz = quizes.find((q) => q.id === quizId);

const currentQuestionIndex = ref(0);
const showResult = ref(false);

const questionPage = computed(() => {
  return `${currentQuestionIndex.value + 1}/${quiz.questions.length}`;
});

const barPercentage = computed(() => {
  const bar = `${
    ((currentQuestionIndex.value + 1) / quiz.questions.length) * 100
  }%`;

  return bar;
});

let numberOfCorrectAnswer = ref(0);

const onSelectOption = (option) => {
  if (option.correct) {
    numberOfCorrectAnswer.value++;
  }
  if (currentQuestionIndex.value === quiz.questions.length - 1) {
    showResult.value = true;
    return;
  }
  currentQuestionIndex.value++;
};
</script>

<template>
  <QuizHeader :questionPage="questionPage" :barPercentage="barPercentage" />
  <QuizContent
    v-if="!showResult"
    :question="quiz.questions[currentQuestionIndex]"
    @selectOption="onSelectOption"
  />
  <QuizResult
    v-else
    :numberOfCorrectAnswer="numberOfCorrectAnswer"
    :totalQuestions="quiz.questions.length"
  />
  <div class="btn-container" v-if="!showResult">
    <button v-if="currentQuestionIndex > 0" @click="currentQuestionIndex--">
      Back
    </button>
    <button
      @click="currentQuestionIndex++"
      v-if="currentQuestionIndex < quiz.questions.length - 1"
    >
      Next
    </button>
    <button
      @click="showResult = true"
      v-if="currentQuestionIndex === quiz.questions.length - 1"
    >
      Show Result
    </button>
  </div>
</template>

<style scoped>
.btn-container {
  display: flex;
  width: 100%;
  gap: 20px;
  justify-content: flex-end;
}
button {
  background-color: #2196f3;
  color: #121212;
  padding: 10px 20px;
  border: none;
  height: 50px;
  width: 120px;
  cursor: pointer;
  font-weight: bold;
  letter-spacing: 1px;
  text-transform: uppercase;
}
</style>
