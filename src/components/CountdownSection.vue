<template>
  <section class="section dark">
    <h2>Menuju Hari Bahagia</h2>
    <div class="time-box">
      <div class="time-item">
        <span class="time-part">{{ days }}</span>
        <span class="time-label">Hari</span>
      </div>
      <div class="time-item">
        <span class="time-part">{{ hours }}</span>
        <span class="time-label">Jam</span>
      </div>
      <div class="time-item">
        <span class="time-part">{{ minutes }}</span>
        <span class="time-label">Menit</span>
      </div>
      <div class="time-item">
        <span class="time-part">{{ seconds }}</span>
        <span class="time-label">Detik</span>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const days = ref('0')
const hours = ref('0')
const minutes = ref('0')
const seconds = ref('0')

const target = new Date('2026-01-07T09:00:00')

onMounted(() => {
  setInterval(() => {
    const diff = target - new Date()
    days.value = Math.floor(diff / 86400000)
    hours.value = Math.floor(diff / 3600000) % 24
    minutes.value = Math.floor(diff / 60000) % 60
    seconds.value = Math.floor(diff / 1000) % 60
  }, 1000)
})
</script>

<style scoped>
.section {
  text-align: center;
  color: #fff;
}

.section.dark {
  background-color: #ffb6c1; /* pink lembut */
  padding: 2rem;
  border-radius: 12px;
}

h2 {
  margin-bottom: 1rem;
  color: white;
}

.time-box {
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 16px;
  flex-wrap: wrap;
}

.time-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
}

.time-part {
  background-color: white;
  color: #ff69b4; /* pink cerah untuk angka */
  padding: 10px 15px;
  border-radius: 8px; /* mempertahankan border radius */
  font-size: 18px;
  font-weight: bold;
  min-width: 40px;
  text-align: center;
}

.time-label {
  font-size: 14px;
  font-weight: bold;
  color: white;
}
</style>
