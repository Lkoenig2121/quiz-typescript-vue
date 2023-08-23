<script setup lang="ts">
  import { ref } from 'vue';
  import QuizCard from './components/QuizCard.vue';
</script>

<template>
  <div class="container">
    <QuizCard />
  </div>
</template>

<style>

* {
  box-sizing: border-box;
}

#app {
  margin: 0;
  padding: 0;
}

body { 
  font-family: 'Merriweather', serif;
  font-family: 'Mukta', sans-serif;
  font-family: 'Roboto Slab', serif;
}

.container {
  background: #bdc3c7; /* For old browsers */
  background: -webkit-linear-gradient(to right, #2c3e50, #bdc3c7); /* Old Google Chrome and Safari */
  background: linear-gradient(to right, #2c3e50, #bdc3c7); /* For newer browsers */
  height: 100vh;
  width: 100vw;
  display: flex;
  align-items: center;
  justify-content: center;
}


</style>