
<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import luffy from '../assets/luffy.gif'
import mrbeast from '../assets/mrbeast-ytpmv.gif'
import kakyoin from '../assets/Kakyoin.png'

const emit = defineEmits(['change-speaker'])

const images = [
  {
    src: luffy,
    title: "Luffy! (à esquerda)",
    legenda: "Soon to be rei dos piratas!"
  },
  {
    src: mrbeast,
    title: "senhor besta",
    legenda: "criador de conteúdo riquíssimo"
  },
  {
    src: kakyoin,
    title: "Kakyoin",
    legenda: "Stand user moderadamente vivo"
  }
]

const currentImage = ref(0)

function selectImage(index){
  currentImage.value = index
  emit('change-speaker', images[index].title)
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
    <div class="imgtxt">
        <h2>{{ images[currentImage].title }}</h2>
        <p>{{ images[currentImage].legenda }}</p>
    </div>
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
  </div>
</template>

<style scoped>
.slideshow {
  position: relative;
  width: 100%;
  max-width: 700px;
  margin: 40px auto;
  overflow: hidden;
  border-radius: 15px;
}

.slide {
  width: 100%;
  height: 400px;
  object-fit: cover;
  display: block;
}

.imgtxt {
  position: relative;
  top: 25px;
}

.imgtxt h2{
  position: relative;
  top: 20px;
  font-family: 'Lexend Exa';
  font-size: 30px;
}
.imgtxt p{
  position: relative;
  top: 460px;
  font-family: 'Lexend Exa';
  font-size: 20px;
}

button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(0, 0, 0, 0.5);
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
  padding: 20px;
  padding-bottom: 60px;
}

</style>