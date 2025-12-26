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
      <button @click="scrollDown">
        Buka Undangan
      </button>
    </div>

    <!-- BUNGA BAWAH -->
    <img src="/images/bunga_kiri.png" class="flower flower-bottom-left" />
    <img src="/images/bunga_kanan.png" class="flower flower-bottom-right" />

    <!-- ===== BUNGA PALING BAWAH TENGAH ===== -->
    <img
      src="/images/bunga_bawah.png"
      class="flower flower-bottom-center"
    />

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
  const target = document.getElementById('opening-section') // ID OpeningSection
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
  font-size: 13px;
  margin-bottom: 18px;
}

.subtitle {
  font-size: 12px;
  letter-spacing: 3px;
}

.title {
  font-family: 'Great Vibes', cursive;
  font-size: 38px;
  margin: 12px 0;
}

.date {
  font-size: 14px;
}

/* ================= BUTTON ================= */
button {
  margin-top: 24px;
  padding: 11px 34px;
  border-radius: 30px;
  border: none;
  background: white;
  font-size: 14px;
  cursor: pointer;
  transition: all .3s ease;
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
  animation: flowerLeft 1.4s ease forwards;
}

.flower-top-right {
  top: -60px;
  right: -50px;
  width: 300px;
  z-index: 4;
  animation: flowerRight 1.4s ease forwards;
}

/* ===== BUNGA BAWAH ===== */
.flower-bottom-left {
  bottom: -70px;              /* ⬅️ sedikit naik */
  left: -50px;
  width: 230px;
  z-index: 6;                 /* ⬅️ DI ATAS bunga tengah */
  animation: flowerBottomLeft 1.6s ease forwards;
}

.flower-bottom-right {
  bottom: -70px;              /* ⬅️ sedikit naik */
  right: -50px;
  width: 230px;
  z-index: 6;                 /* ⬅️ DI ATAS bunga tengah */
  animation: flowerBottomRight 1.6s ease forwards;
}

/* ===== BUNGA PALING BAWAH TENGAH ===== */
.flower-bottom-center {
  position: absolute;
  bottom: -40px;
  left: 0;
  right: 0;
  margin: 0 auto;       /* ⬅️ CENTER KIRI–KANAN */
  width: 110%;
  max-width: 480px;
  z-index: 4;
  opacity: 1;
  pointer-events: none;
}



/* ================= ANIMATIONS ================= */
@keyframes fadeUp {
  from {
    opacity: 0;
    transform: translateY(25px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes houseUp {
  from {
    opacity: 0;
    transform: translate(-50%, 70px);
  }
  to {
    opacity: 1;
    transform: translate(-50%, 0);
  }
}

@keyframes flowerLeft {
  from {
    opacity: 0;
    transform: translate(-50px, -20px);
  }
  to {
    opacity: 1;
    transform: translate(0, 0);
  }
}

@keyframes flowerRight {
  from {
    opacity: 0;
    transform: translate(50px, -20px);
  }
  to {
    opacity: 1;
    transform: translate(0, 0);
  }
}

@keyframes flowerBottomLeft {
  from {
    opacity: 0;
    transform: translate(-40px, 50px);
  }
  to {
    opacity: 1;
    transform: translate(0, 0);
  }
}

@keyframes flowerBottomRight {
  from {
    opacity: 0;
    transform: translate(40px, 50px);
  }
  to {
    opacity: 1;
    transform: translate(0, 0);
  }
}

/* ================= ANIMASI BUNGA BERGOYANG HALUS ================= */
.flower {
  transform-origin: center top;
  animation:
    sway 12s ease-in-out infinite alternate;
}

/* Beda timing biar natural */
.flower-top-left {
  animation:
    flowerLeft 1.4s ease forwards,
    sway 13s ease-in-out infinite alternate;
}

.flower-top-right {
  animation:
    flowerRight 1.4s ease forwards,
    swayReverse 14s ease-in-out infinite alternate;
}

.flower-bottom-left {
  animation:
    flowerBottomLeft 1.6s ease forwards,
    sway 15s ease-in-out infinite alternate;
}

.flower-bottom-right {
  animation:
    flowerBottomRight 1.6s ease forwards,
    swayReverse 16s ease-in-out infinite alternate;
}

/* ================= KEYFRAMES GOYANG ================= */
@keyframes sway {
  0% {
    transform: rotate(-1.5deg) translateY(0);
  }
  50% {
    transform: rotate(1.5deg) translateY(4px);
  }
  100% {
    transform: rotate(-1.5deg) translateY(0);
  }
}

@keyframes swayReverse {
  0% {
    transform: rotate(1.5deg) translateY(0);
  }
  50% {
    transform: rotate(-1.5deg) translateY(4px);
  }
  100% {
    transform: rotate(1.5deg) translateY(0);
  }
}
</style>