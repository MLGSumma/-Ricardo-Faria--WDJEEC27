
<script setup>
import { ref } from 'vue'

const comment = ref('')
const comments = ref([])

function addComment() {
  if (comment.value.trim() === '') return

  comments.value.push({
    id: Date.now(),
    text: comment.value
  })

  comment.value = ''
}
</script>

<template>
  <div class="comment-section">
    <h2>Opiniões</h2>

    <textarea
      v-model="comment"
      placeholder="Escreva uma opinião!..."
    ></textarea>

    <button @click="addComment">
      Enviar
    </button>

    <h3>Opiniões ({{ comments.length }})</h3>

    <div
      v-for="item in [...comments].reverse()"
      :key="item.id"
      class="comment"
    >
      {{ item.text }}
    </div>
  </div>
</template>

<style scoped>

.comment-section {
  display: flex;
  flex-direction: column;
  width: 100%;
  max-width: 1000px;
  text-align: center;
  padding: 200px;
  box-sizing: border-box;
  margin-inline: auto;
  
}
  
textarea {
  width: 100%;
  min-height: 100px;
  padding: 12px;
  border-radius: 12px;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

button {
  margin-top: 10px;
  padding: 10px 25px;
  border: none;
  border-radius: 999px;
  background: #2563eb;
  color: white;
  cursor: pointer;
  transition: 0.3s;
}

button:hover {
  background: #60a5fa;
  box-shadow: 0 0 15px #60a5fa;
}

.comment {
  background: #eee;
  color: #222;
  padding: 12px;
  margin-top: 10px;
  border-radius: 10px;
  overflow-wrap: anywhere;
}
</style>
