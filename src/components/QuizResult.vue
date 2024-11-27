<script setup>
import { RouterLink } from "vue-router";
const { numberOfCorrectAnswer, totalQuestions } = defineProps([
  "numberOfCorrectAnswer",
  "totalQuestions",
]);

const result = (numberOfCorrectAnswer / totalQuestions) * 100;
</script>

<template>
  <div class="result">Result : {{ result }}</div>
  <RouterLink to="/" class="btn">Go Back</RouterLink>
</template>

<style scoped>
.result {
  padding: 20px 10px;
}
.btn {
  margin-top: 80px;
  background-color: #2196f3;
  text-decoration: none;
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
