
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import luffy from '../assets/luffy.gif'
import mrbeast from '../assets/mrbeast-ytpmv.gif'
import kakyoin from '../assets/Kakyoin.png'

const emit = defineEmits(['change-speaker'])

onMounted(() => {
  emit('change-speaker', images[currentImage.value].votetext)
})

const images = [
  {
    src: luffy,
    title: "Luffy! (à esquerda)",
    legenda: "Soon to be rei dos piratas!",
    votetext: "Luffy"
  },
  {
    src: mrbeast,
    title: "Senhor Besta",
    legenda: "Criador de conteúdo riquíssimo.",
    votetext: "Sr Besta"
  },
  {
    src: kakyoin,
    title: "Kakyoin",
    legenda: "Stand user moderadamente vivo...",
    votetext: "Kakyoin"
  }
]

const currentImage = ref(0)

function selectImage(index){
  currentImage.value = index
  emit('change-speaker', images[index].votetext)
}

function nextImage() {
  selectImage((currentImage.value + 1) % images.length)
}

function previousImage() {
  selectImage((currentImage.value - 1 + images.length) % images.length)
}

</script>

<template>
  <div class="imagescontainer">
    <h2>{{ images[currentImage].title }}</h2>
    <div class="slideshow">
      <img
        :src="images[currentImage].src"
        alt="Slideshow image"
        class="slide"
      />

      <button class="prev" @click="previousImage">
        &#10094;
      </button>

      <button class="next" @click="nextImage">
        &#10095;
      </button>

      <div class="dots">
        <span
          v-for="(image, index) in images"
          :key="index"
          :class="{ active: currentImage === index }"
          @click="currentImage = index"
        ></span>
      </div>
    </div>
    
    <p>{{ images[currentImage].legenda }}</p>
  </div>
</template>

<style scoped>
.slideshow {
  position: relative;
  width: 100%;
  max-width: 400px;
  overflow: hidden;
  border-radius: 15px;
}

.slide {
  width: 100%;
  height: 400px;
  object-fit: cover;
  display: block;
  flex-shrink: 0;
  flex-grow: 0;
}

h2{
  font-family: 'Lexend Exa';
  font-size: 30px;
}
p{
  font-family: 'Lexend Exa';
  font-size: 20px;
}

button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.871);
  color: white;
  border: none;
  padding: 15px;
  cursor: pointer;
  font-size: 20px;
  border-radius: 8px;
}

button:hover {
  background: rgba(0, 0, 0, 0.8);
}

.prev {
  left: 10px;
}

.next {
  right: 10px;
}

.dots {
  position: absolute;
  bottom: 15px;
  width: 100%;
  display: flex;
  justify-content: center;
  gap: 10px;
}

.dots span {
  width: 12px;
  height: 12px;
  background: white;
  opacity: 0.5;
  border-radius: 50%;
  cursor: pointer;
}

.dots span.active {
  opacity: 1;
  background: #0980ff;
}
</style>

<style>
.imagescontainer{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 20px;
}

</style>