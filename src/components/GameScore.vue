<script setup>
const props=defineProps(['userAlternative', 'computerAlternative', 'winnerInfo'])

</script>

<template>

    <div v-if="props.winnerInfo!==''" id="resultat">
        <p>Du valde {{ props.userAlternative }}</p><br>
        <p>Datorn valde {{ props.computerAlternative }}</p><br>
        <p>{{ props.winnerInfo }}</p>
    </div>

</template>

<style scoped>
#resultat p {
  border:2px solid black;
  margin:auto;
  padding:0.5em;
  width:50%;
  background-color:aqua;
  text-align:center;
  color: black;
}
</style>