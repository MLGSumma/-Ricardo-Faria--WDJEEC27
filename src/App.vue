<script setup>
import { ref, onMounted} from 'vue'
import commentbox from './components/commentbox.vue'
import images from './components/Imagens.vue'
const title = ref('My First Website')

function buttonpress(){
  console.log("votar!");
}

</script>

<template>
  <div class="container">
  <h1>JEEC</h1>
  <h2>Speakers</h2>
  <images></images>
  <button @click="buttonpress" class = "voteButton">VOTAR</button>
  <h3>Vota num dos 3 speakers!</h3>
  <commentbox></commentbox>
  </div>
</template>

<style scoped>
.container {
  text-align: center;
  margin-top: 100px;
  font-family: Arial, sans-serif;
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
  margin-block: 60px;
  font-family: Lexend Exa;
  color: #ffffff;
  font-size: 65px;
    text-shadow: 0 0 10px #0980ff,
               0 0 20px #ffffff,
               0 0 40px #ffffff;
}

h3 {
  margin-block: 60px;
  font-family: Lexend Exa;
  color: #ffffff;
  font-size: 35px;
    text-shadow: 0 0 10px #0980ff,
               0 0 20px #ffffff,
               0 0 40px #ffffff;
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

.voteButton:hover{
  background-color: rgba(138, 138, 184, 0.294);
  transform: scale(1.05);
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
</style>
