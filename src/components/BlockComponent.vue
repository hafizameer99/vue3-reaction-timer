<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        CLick Me
    </div>
</template>

<script setup>
import { onMounted, ref, defineProps, defineEmits } from "vue";

    const emits = defineEmits(['customEvent']);
    const props = defineProps({
    delay: {
        type: String,
    }
    });
    const timer = ref(null)
    const reactionTime = ref(0)
    const showBlock = ref(false)
    onMounted(() => {
        setTimeout(() => {
            showBlock.value = true;
            startTimer()
        }, props.delay)
    })

    const startTimer = () => {
        timer.value = setInterval(() => {
            reactionTime.value += 10 
        }, 10);
    }
    const stopTimer = () => {
        clearInterval(timer.value)
        emits('end',reactionTime.value)
    }

</script>

<style scoped>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0faf87;
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>
