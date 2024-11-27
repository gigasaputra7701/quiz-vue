<template>
  <main>
    <RouterView />
  </main>
</template>

<script setup>
import { RouterView } from "vue-router";
</script>

<style scoped>
main {
  max-width: 900px;
  margin: 0 auto;
}
</style>
