<script setup>
import { defineProps, ref, watch } from 'vue'

const prop=defineProps(['result'])
const userScore = ref(0)
const computerScore = ref(0)

watch(prop, () => {
    if (prop.result.winner === 'user') {
        userScore.value++
    } else if (prop.result.winner === 'computer') {
        computerScore.value++
    }
    
})
</script>

<template>
<div v-if="computerScore || userScore">
    <span id="userScore">
        <span :class="userScore>computerScore ? 'leader score' : score"> {{ userScore }} </span>
    <p>User</p>
    </span>
    <span id="computerScore"> 
        <span :class="computerScore>userScore ? 'leader score' : score"> {{ computerScore }} </span>
    <p>Computer</p>
    </span>
</div>
</template>

<style scoped>
div {
    margin:auto;
    padding: 0,5em;
    width: 50%;
}

.score{
    background-color: rgb(27, 28, 28);
    font-size: 3em;
    display: inline-block;
    text-align: center;
    margin: 0,2em;
}
.leader{
    color: blue;
    font-size: 5em;
    
}
</style>