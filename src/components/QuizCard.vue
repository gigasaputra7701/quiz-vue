<script setup>
import { useRouter } from "vue-router";

const { quiz } = defineProps(["quiz"]);

const router = useRouter();

const goToQuiz = () => {
  router.push({
    name: "quiz",
    params: {
      id: quiz.id,
    },
  });
};
</script>

<template>
  <div class="card" @click="goToQuiz">
    <div class="card-img-container">
      <img class="card-img" :src="quiz.img" alt="" />
    </div>
    <div class="card-body">
      <h2>{{ quiz.title }}</h2>
      <p>Questions: {{ quiz.questions.length }}</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 250px;
  border-radius: 5px;
  overflow: hidden;
  background-color: rgba(255, 255, 255, 0.12);
  transition: all 300ms ease-in-out;
  cursor: pointer;
}
.card:hover img {
  transition: all 300ms ease-in-out;
  transform: scale(1.05);
}
.card:hover {
  background-color: rgba(255, 255, 255, 0.08);
  transition: all 300ms ease-in-out;
}
.card:active {
  background-color: rgba(255, 255, 255, 0.16);
}
.card-img-container {
  overflow: hidden;
  width: 250px;
  height: 250px;
}
.card-body {
  padding: 6px 12px;
}
.card-img {
  width: 250px;
  height: 250px;
  object-fit: cover;
  transition: all 300ms ease-in-out;
  background-position: center;
}
.card-body h2 {
  color: rgba(255, 255, 255, 0.9);
}
.card-body p {
  margin-top: 24px;
  color: rgba(255, 255, 255, 0.7);
}
</style>
