<script setup>
import { ref, onMounted} from 'vue'
import commentbox from './components/commentbox.vue'
import images from './components/Imagens.vue'
import vote from './components/Vote.vue'
import calendar from './components/Datepicker.vue'
import info from './components/Info.vue'

const title = ref('My First Website')

function buttonpress(){
  console.log("votar!");
}

const currentSpeaker = ref('')

</script>

<template>
  <div class="container">
    <div class="title">
      <h1>JEEC</h1>
      <h2>Speakers</h2>
      
    </div>
    
    <div class="sideways">
      <calendar></calendar>
      <div class="voting">
        <h3>Vota num dos 3 speakers!</h3>
        <images @change-speaker="currentSpeaker = $event" />
        <vote :speaker="currentSpeaker" />
      </div>
    </div>
    <info></info>
    <commentbox></commentbox>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
  margin-top: 50px;
  font-family: Arial, sans-serif;
  display: flex;
  flex-direction: column;
  gap: 70px;
}

h1 {
  font-family: Lexend Exa;
  color: #0980ff;
  font-size: 150px;
  text-shadow: 0 0 10px #ffffff,
               0 0 10px #ffffff,
               0 0 40px #ffffff;
}

h2 {
  font-family: Lexend Exa;
  color: #ffffff;
  font-size: 65px;
  text-shadow: 0 0 10px #0980ff,
               0 0 20px #ffffff,
               0 0 40px #ffffff;
}

h3 {
  font-family: Lexend Exa;
  color: #ffffff;
  font-size: 35px;
  text-shadow: 0 0 10px #0980ff,
               0 0 20px #ffffff,
               0 0 40px #ffffff;
}

</style>


<style>

@font-face {
  font-family: 'Lexend Exa';
  src: url('https://fonts.gstatic.com/s/lexendexa/v35/UMBCrPdOoHOnxExyjdBeQCH18mulUxBvI9ocSZbAFp4.woff2') format('woff2');
}

body {
  background-color: rgba(5, 0, 136, 0.213);
  border-left: none;
  border-right: none;
}
#app {
  border-left: none;
  border-right: none;
}

.title {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  gap: 25px;
}

.voting {
  display: flex;
  flex-direction: column;
  flex: 1;
  gap: 55px;
}




.sideways {
  display: flex;
  flex-direction: row;
  gap: 200px;
  align-items: center;
  justify-content: center;
}

</style>
