<script setup>
import { ref } from 'vue'

const date = ref(new Date())
const showCalendar = ref(false)

function toggleCalendar() {
  showCalendar.value = !showCalendar.value
}
</script>

<template>
  <div class="calendar-container">
    <h2>
      Reserve aqui o bilhete diário para o JEEC 2027!
    </h2>
    <button @click="toggleCalendar">Reservar Bilhete!</button>
    <div v-if="showCalendar">
      <VDatePicker
        v-model="date"
        mode="date"
        :min-date="new Date()"
      />
    </div>
    <p>
      Dia selecionado: {{ date.toLocaleDateString('pt-PT') }}
    </p>

  </div>
</template>

<style scoped>
.calendar-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 50px;
  margin: 50px auto;
  max-width: 400px;
}

p {
  font-family: 'Lexend Exa';
}

h2 {
    font-family: Lexend Exa;
  color: #ffffff;
  font-size: 25px;
  text-shadow: 0 0 10px #0980ff,
               0 0 20px #ffffff,
               0 0 40px #ffffff;
}

button {
  border-style: solid;
  border-width: 1px;
  border-radius: 8px;
  scale: 3;
  background-color: rgba(0, 0, 255, 0.294);
  font-family: 'Lexend Exa';
  padding: 3px;
  line-height: .8;
}

.voteButton.voted {
  background: #777;
  cursor: not-allowed;
}

button:hover {
  background: #60a5fa;
  box-shadow: 0 0 15px #60a5fac8;
  transform: scale(1.05);
}
</style>