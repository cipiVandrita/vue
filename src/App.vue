<template>
  <div>
    <h1>Sten Sax Påse</h1><br>
    <GameAlternatives 
      @user-choice="setUserAlternative" 
      @computer-choice="setComputerAlternative" 
      @winner="setWinnerInfo"
    />
    <GameScore 
      :user-alternative="alternative" 
      :computer-alternative="compAlternative" 
      :winner-info="winnerInfo"
    />
    <GameResult :result="{ round, winner }"/>
    
    <!-- Lägg till en reset-knapp -->
    <button class="reset" @click="resetGame">Återställ spelet</button>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import GameAlternatives from './components/GameAlternatives.vue'
import GameScore from './components/GameScore.vue'
import GameResult from './components/GameResult.vue'

const alternative = ref("")
const compAlternative = ref('')
const winnerInfo = ref('')
const winner = ref('')
const round = ref(0)

function setWinnerInfo(_winner) {
  winner.value = _winner
  round.value++
  if (_winner === "draw") {
    winnerInfo.value = "Det är lika"
  } else if (_winner === "user") {
    winnerInfo.value = "Du vann"
  } else {
    winnerInfo.value = "Du förlorade" 
  }
}

function setUserAlternative(alt) {
  alternative.value = alt
}

function setComputerAlternative(alt) {
  compAlternative.value = alt
}

// Funktion för att återställa spelet
function resetGame() {
  alternative.value = ""
  compAlternative.value = ""
  winnerInfo.value = ""
  winner.value = ""
  round.value = 0
  location.reload();
}
</script>

<style scoped>
.reset {
  list-style-type: none;
  margin:0.5em;
  background-color:rgb(99, 86, 86);
  padding:1em;
  border:2px solid black;
  border-radius:0.5em;
  color: black; 
}

h1 {
  text-align:center;
  min-width:10px;
}
</style>
