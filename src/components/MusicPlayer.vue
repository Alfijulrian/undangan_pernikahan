<template>
  <button class="music-btn" @click="toggleMusic">
    <span v-if="isPlaying">🔊</span>
    <span v-else>🔇</span>
  </button>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isPlaying = ref(false)

// Buat audio global jika belum ada
if (!window.bgMusic) {
  window.bgMusic = new Audio('/audio/lagu_cintaterakhir.mp3')
  window.bgMusic.loop = true
}

// Fungsi toggle musik manual
const toggleMusic = async () => {
  if (window.bgMusic.paused) {
    await window.bgMusic.play()
    isPlaying.value = true
  } else {
    window.bgMusic.pause()
    isPlaying.value = false
  }
}

// Play otomatis saat tombol Buka Undangan diklik
onMounted(() => {
  document.addEventListener('startMusic', async () => {
    if (window.bgMusic.paused) {
      await window.bgMusic.play()
      isPlaying.value = true
    }
  })
})
</script>

<style scoped>
.music-btn {
  position: fixed;
  bottom: 20px;
  right: 20px;
  width: 55px;
  height: 55px;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  font-size: 22px;
  background: rgba(255, 255, 255, 0.9);
  box-shadow: 0 6px 15px rgba(0,0,0,0.25);
  transition: transform 0.2s ease;
  z-index: 999;
}

.music-btn:hover {
  transform: scale(1.1);
}
</style>
