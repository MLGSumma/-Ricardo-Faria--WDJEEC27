<script setup>
import { ref, watch, onUnmounted } from 'vue'

const props = defineProps({
  speaker: {
    type: String,
    required: true
  }
})



const hasVoted = ref(false)
const showPopup = ref(false)
const votedSpeaker = ref('')

function vote() {
  if (hasVoted.value) return

  showPopup.value = true
  scroll()
}

function confirmVote() {
  votedSpeaker.value = props.speaker
  hasVoted.value = true
  showPopup.value = false

  console.log('Voto para:', votedSpeaker.value, "contado")
}

function cancelVote() {
  showPopup.value = false
}

watch(showPopup, (isOpen) => {
  document.documentElement.style.overflow = isOpen ? 'hidden' : ''
})

onUnmounted(() => {
  document.documentElement.style.overflow = ''
})


</script>

<template>
  <div class="voting-container">

    <button
      class="voteButton"
      :class="{ 'voted': hasVoted }"
      @click="vote"
      :disabled="hasVoted"
    >
      {{ hasVoted ? 'Voto Registado' : 'Votar' }}
    </button>
    
    <p v-if="!hasVoted">
      (carrega no botão "votar" na imagem de quem pretende votar!)
    </p>

    <p v-if="hasVoted" class="vote-status">
      Votaste {{ votedSpeaker }}!
    </p>

    <div v-if="showPopup" class="popup-overlay">
      <div class="popup">

        <h2>Confirma o voto</h2>

        <p>
          Queres votar
          <strong>{{ speaker }}</strong>?
        </p>

        <div class="popup-buttons">
          <button class="confirm" @click="confirmVote">
            Confirmar
          </button>

          <button class="cancel" @click="cancelVote">
            Cancelar
          </button>
        </div>

      </div>
    </div>

  </div>
</template>



<style scoped>
.voting-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

.voting-container p{
  position: relative;
  top: 35px;
  padding: 5px;
}

.voteButton{
  border-style: solid;
  border-width: 1px;
  border-radius: 8px;
  scale: 4;
  background-color: rgba(0, 0, 255, 0.294);
  font-family: 'Lexend Exa';
  padding: 3px;
  line-height: .8;
  
}

.voteButton:hover:not(.voted){
  background: #60a5fa;
  box-shadow: 0 0 15px #60a5fac8;
  transform: scale(1.05);
}

.voteButton.voted {
  background: #777;
  cursor: not-allowed;
}

.vote-status {
  color: white;
  font-family: 'Lexend Exa';
}

.popup-overlay {
  position: fixed;
  inset: 0;
  z-index: 9999;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.7);
}

.popup {
  background: rgb(255, 255, 255);
  color: #222;
  padding: 30px;
  border-radius: 20px;
  width: 90%;
  max-width: 400px;
  text-align: center;
  box-sizing: border-box;
}

.popup h2 {
  font-family: 'Lexend Exa';
  font-size: 24px;
  color: #777;
}

.popup p {
  position: relative;
  top: 5px;
  font-family: 'Lexend Exa';
  font-size: 24px;
}

p {
  font-family: 'Lexend Exa';
  font-size: 20px;
}


.popup-buttons {
  display: flex;
  flex-direction: row;
  justify-content: center;
  gap: 15px;
  margin-top: 25px;
}

.popup-buttons button {
  padding: 10px 20px;
  border: none;
  border-radius: 20px;
  color: white;
  cursor: pointer;
}

.confirm {
  background: #0980ff;
  font-family: 'Lexend Exa';
}

.cancel {
  background: #777;
  font-family: 'Lexend Exa';
}
</style>