<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Result v-if="showResults" :score="score"/>

</template>

<script setup>
  import { ref } from "vue"
import Block from "./components/BlockComponent.vue";
import Result from "./components/ResultsComponent.vue";

    const isPlaying = ref(false);
    const delay = ref(null);
    const score = ref(null);
    const showResults = ref(false)

    const start = () => {
      delay.value = 2000 + Math.random() * 5000;
      isPlaying.value = true;
      showResults.value = false;
    };
    const endGame = (reactionTime) => {
      score.value = reactionTime;
      isPlaying.value = false;
      showResults.value = true;
    }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
