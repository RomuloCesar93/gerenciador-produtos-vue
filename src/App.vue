<script setup>
import { ref } from "vue";
const nome = ref("");
</script>

<template>
  <h1>Gerenciador de tarefas!</h1>
  <input type="text" v-model="nome" />

  <p>{{ nome }}</p>
</template>

<style scoped></style>
