<template>
<div>
  <p>Reaction Time - {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</div>
</template>
<script setup>
import { onMounted, defineProps, ref } from "vue";

const props = defineProps({
    score: {
        type: Number,
    }
});
    const rank = ref(null)
    onMounted(() => {
        if(props.score < 250) {
            rank.value = 'Ninga Fingers';
        } else if (props.score < 400) {
            rank.value = 'Rapid Reflexes';
        } else {
            rank.value = 'Snail Pace...';
        }
    });
</script>
<style scoped>
    .rank{
        font-size: 1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>