<script setup>
import { defineProps } from "vue";

const { questionPage, barPercentage } = defineProps([
  "questionPage",
  "barPercentage",
]);
</script>

<template>
  <header>
    <h4>Question: {{ questionPage }}</h4>
    <div class="bar">
      <div class="bar-progress" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
}
header h4 {
  font-size: 30px;
}
.bar {
  width: 100%;
  height: 15px;
  border: 2px solid #2196f3;
  border-radius: 20px;
  overflow: hidden;
}
.bar-progress {
  height: 100%;
  width: 50%;
  background-color: #2196f3;
}
</style>
