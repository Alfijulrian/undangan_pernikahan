<template>
  <section class="hero">
    <div class="bg-blur"></div>

    <!-- BUNGA ATAS -->
    <img src="/images/bunga_kiri_atas.png" class="flower flower-top-left" />
    <img src="/images/bunga_kanan_atas.png" class="flower flower-top-right" />

    <!-- KONTEN -->
    <div class="content">
      <p class="guest">
        Kepada Yth<br />
        {{ guest }}
      </p>

      <h3 class="subtitle">The Wedding Of</h3>
      <h1 class="title">Aldes & Suci</h1>
      <p class="date">08 Januari 2026</p>

      <!-- FIXED BUTTON -->
      <button @click="scrollDown">Buka Undangan</button>
    </div>

    <!-- BUNGA BAWAH -->
    <img src="/images/bunga_kiri.png" class="flower flower-bottom-left" />
    <img src="/images/bunga_kanan.png" class="flower flower-bottom-right" />

    <!-- BUNGA PALING BAWAH TENGAH -->
    <img src="/images/bunga_bawah.png" class="flower flower-bottom-center" />

    <!-- RUMAH -->
    <img src="/images/rumah_melayu.webp" class="rumah" />
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const guest = ref('Tamu Undangan')

onMounted(() => {
  const params = new URLSearchParams(window.location.search)
  if (params.get('to')) {
    guest.value = decodeURIComponent(params.get('to'))
  }
})

// Scroll langsung ke OpeningSection saat klik tombol
const scrollDown = () => {
  const target = document.getElementById('opening-section')
  if (target) {
    target.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<style scoped>
/* ================= HERO ================= */
.hero {
  position: relative;
  min-height: 100vh;
  background: url('/images/danau_raja.jpg') center / cover no-repeat;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  overflow: hidden;
}

/* ================= BLUR ================= */
.bg-blur {
  position: absolute;
  inset: 0;
  background:
    linear-gradient(rgba(0,0,0,.45), rgba(0,0,0,.7)),
    url('/images/danau_raja.jpg') center / cover no-repeat;
  filter: blur(6px);
  transform: scale(1.1);
  z-index: 0;
}

/* ================= KONTEN ================= */
.content {
  position: relative;
  z-index: 5;
  color: white;
  padding: 0 20px;
  animation: fadeUp 1.3s ease forwards;
}

.guest {
  font-size: 14px;
  margin-bottom: 18px;
}

.subtitle {
  font-size: 16px;
  letter-spacing: 3px;
}

.title {
  font-family: 'Great Vibes', cursive;
  font-size: 48px; /* Lebih besar */
  margin: 12px 0;
}

.date {
  font-size: 16px;
  margin-bottom: 20px;
}

/* ================= BUTTON ================= */
button {
  margin-top: 24px;
  padding: 12px 36px;
  border-radius: 30px;
  border: none;
  background: white;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 20px rgba(0,0,0,.25);
}

/* ================= RUMAH ================= */
.rumah {
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 380px;
  max-width: 90vw;
  z-index: 10;
  pointer-events: none;
  opacity: 0;
  animation: houseUp 1.6s ease forwards;
  animation-delay: .4s;
}

/* ================= BUNGA UMUM ================= */
.flower {
  position: absolute;
  opacity: 0;
  pointer-events: none;
}

/* ===== BUNGA ATAS ===== */
.flower-top-left {
  top: -60px;
  left: -50px;
  width: 300px;
  z-index: 4;
  animation: flowerLeft 1.4s ease forwards, sway 13s ease-in-out infinite alternate;
}

.flower-top-right {
  top: -60px;
  right: -50px;
  width: 300px;
  z-index: 4;
  animation: flowerRight 1.4s ease forwards, swayReverse 14s ease-in-out infinite alternate;
}

/* ===== BUNGA BAWAH ===== */
.flower-bottom-left {
  bottom: -70px;
  left: -50px;
  width: 230px;
  z-index: 6;
  animation: flowerBottomLeft 1.6s ease forwards, sway 15s ease-in-out infinite alternate;
}

.flower-bottom-right {
  bottom: -70px;
  right: -50px;
  width: 230px;
  z-index: 6;
  animation: flowerBottomRight 1.6s ease forwards, swayReverse 16s ease-in-out infinite alternate;
}

/* ===== BUNGA PALING BAWAH TENGAH ===== */
.flower-bottom-center {
  bottom: -40px;
  left: 0;
  right: 0;
  margin: 0 auto;
  width: 110%;
  max-width: 480px;
  z-index: 4;
  opacity: 1;
}

/* ================= ANIMASI ================= */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(25px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes houseUp {
  from { opacity: 0; transform: translate(-50%, 70px); }
  to { opacity: 1; transform: translate(-50%, 0); }
}

@keyframes flowerLeft {
  from { opacity: 0; transform: translate(-50px, -20px); }
  to { opacity: 1; transform: translate(0, 0); }
}

@keyframes flowerRight {
  from { opacity: 0; transform: translate(50px, -20px); }
  to { opacity: 1; transform: translate(0, 0); }
}

@keyframes flowerBottomLeft {
  from { opacity: 0; transform: translate(-40px, 50px); }
  to { opacity: 1; transform: translate(0, 0); }
}

@keyframes flowerBottomRight {
  from { opacity: 0; transform: translate(40px, 50px); }
  to { opacity: 1; transform: translate(0, 0); }
}

/* ================= GOYANG HALUS ================= */
@keyframes sway {
  0% { transform: rotate(-1.5deg) translateY(0); }
  50% { transform: rotate(1.5deg) translateY(4px); }
  100% { transform: rotate(-1.5deg) translateY(0); }
}

@keyframes swayReverse {
  0% { transform: rotate(1.5deg) translateY(0); }
  50% { transform: rotate(-1.5deg) translateY(4px); }
  100% { transform: rotate(1.5deg) translateY(0); }
}

/* ================= RESPONSIF MOBILE ================= */
@media (max-width: 768px) {
  .subtitle { font-size: 18px; }
  .title { font-size: 36px; } /* diperbesar di mobile */
  .date { font-size: 18px; }
  .guest { font-size: 16px; }
  button { font-size: 16px; padding: 12px 36px; }
}
</style>
