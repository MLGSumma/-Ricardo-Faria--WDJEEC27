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
  gap: 30px;
  margin: 50px auto;
}

p {
  font-family: 'Lexend Exa';
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
  background-color: rgba(138, 138, 184, 0.294);
  transform: scale(1.05);
}
</style>