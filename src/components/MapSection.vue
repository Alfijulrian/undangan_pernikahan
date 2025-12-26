<template>
  <button class="music-btn" @click="toggleMusic">
    <span v-if="isPlaying">🔊</span>
    <span v-else>🔇</span>
  </button>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const isPlaying = ref(false)

// Buat audio global sekali
if (!window.bgMusic) {
  window.bgMusic = new Audio('/audio/SnapTik.Net_7502658448908111110.mp3')
  window.bgMusic.loop = true
}

// Fungsi toggle musik
const toggleMusic = async () => {
  if (!window.bgMusic) return

  if (window.bgMusic.paused) {
    try {
      await window.bgMusic.play()
      isPlaying.value = true
    } catch (err) {
      console.log('Autoplay gagal:', err)
    }
  } else {
    window.bgMusic.pause()
    isPlaying.value = false
  }
}

// Coba autoplay saat halaman pertama dimuat
onMounted(async () => {
  try {
    if (window.bgMusic.paused) {
      await window.bgMusic.play()
      isPlaying.value = true
    }
  } catch (err) {
    console.log('Autoplay gagal, tunggu interaksi user')
  }
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
