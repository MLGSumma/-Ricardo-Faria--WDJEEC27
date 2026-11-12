<script setup>
import { ref, onMounted} from 'vue'
import mrbeast from './assets/mrbeast-ytpmv.gif'
import luffy from './assets/luffy.gif'
const title = ref('My First Website')

</script>

<template>
  <div class="container">
  <h1>JEEC</h1>
  <h2>Speakers</h2>
  
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
</style>


<style>

@font-face {
  font-family: 'Lexend Exa';
  src: url('https://fonts.gstatic.com/s/lexendexa/v35/UMBCrPdOoHOnxExyjdBeQCH18mulUxBvI9ocSZbAFp4.woff2') format('woff2');
}

body {
  background-color: rgba(16, 11, 167, 0.213);
  border-left: none;
  border-right: none;
}
#app {
  border-left: none;
  border-right: none;
}
</style>
