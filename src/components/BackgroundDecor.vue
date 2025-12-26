<template>
  <div class="background-decor" ref="decor">
    <div class="bg-blur"></div>

    <!-- Bunga atas -->
    <img src="/images/bunga_kiri_atas.png" class="flower flower-top-left" />
    <img src="/images/bunga_kanan_atas.png" class="flower flower-top-right" />

    <!-- Bunga bawah -->
    <img src="/images/bunga_kiri.png" class="flower flower-bottom-left" />
    <img src="/images/bunga_kanan.png" class="flower flower-bottom-right" />

    <!-- Bunga paling bawah tengah -->
    <img src="/images/bunga_bawah.png" class="flower flower-bottom-center" />

    <!-- Rumah -->
    <img src="/images/rumah_melayu.webp" class="rumah" />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const decor = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          // Tambahkan class 'animate' saat terlihat
          decor.value.classList.add('animate')
        }
      })
    },
    {
      threshold: 0.2 // 20% sudah terlihat
    }
  )

  if (decor.value) observer.observe(decor.value)
})
</script>

<style scoped>
.background-decor {
  position: absolute;
  inset: 0;
  z-index: 0;
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

/* ================= RUMAH ================= */
.rumah {
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%) translateY(70px);
  width: 380px;
  max-width: 90vw;
  z-index: 10;
  pointer-events: none;
  opacity: 0;
  transition: all 1.6s ease;
}

/* ================= BUNGA UMUM ================= */
.flower {
  position: absolute;
  pointer-events: none;
  opacity: 0;
  transform-origin: center top;
  transition: all 1.6s ease;
}

/* Bunga atas */
.flower-top-left { top: -60px; left: -50px; width: 300px; z-index: 4; }
.flower-top-right { top: -60px; right: -50px; width: 300px; z-index: 4; }

/* Bunga bawah */
.flower-bottom-left { bottom: -70px; left: -50px; width: 230px; z-index: 6; }
.flower-bottom-right { bottom: -70px; right: -50px; width: 230px; z-index: 6; }

/* Bunga bawah tengah */
.flower-bottom-center {
  bottom: -40px;
  left: 0; right: 0;
  margin: 0 auto;
  width: 110%;
  max-width: 480px;
  z-index: 4;
}

/* ================= ANIMASI SAAT SCROLL ================= */
.background-decor.animate .flower-top-left { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: sway 12s ease-in-out infinite alternate, flowerEnterLeft 1s ease forwards; 
}

.background-decor.animate .flower-top-right { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: swayReverse 13s ease-in-out infinite alternate, flowerEnterRight 1s ease forwards; 
}

.background-decor.animate .flower-bottom-left { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: sway 14s ease-in-out infinite alternate, flowerEnterBottomLeft 1s ease forwards; 
}

.background-decor.animate .flower-bottom-right { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: swayReverse 15s ease-in-out infinite alternate, flowerEnterBottomRight 1s ease forwards; 
}

.background-decor.animate .flower-bottom-center { 
  opacity: 1; 
  transform: translateY(0); 
  animation: sway 16s ease-in-out infinite alternate, flowerEnterCenter 1s ease forwards; 
}

.background-decor.animate .rumah { 
  opacity: 1; 
  transform: translateX(-50%) translateY(0); 
  animation: houseUp 1.6s ease forwards;
}
/* ================= KEYFRAMES GOYANG HALUS ================= */
@keyframes sway {
  0% { transform: rotate(-2deg) translateY(0px); }
  25% { transform: rotate(1.5deg) translateY(-1px); }
  50% { transform: rotate(2deg) translateY(0px); }
  75% { transform: rotate(-1.5deg) translateY(1px); }
  100% { transform: rotate(-2deg) translateY(0px); }
}

@keyframes swayReverse {
  0% { transform: rotate(2deg) translateY(0px); }
  25% { transform: rotate(-1.5deg) translateY(1px); }
  50% { transform: rotate(-2deg) translateY(0px); }
  75% { transform: rotate(1.5deg) translateY(-1px); }
  100% { transform: rotate(2deg) translateY(0px); }
}

/* ================= ANIMASI SAAT SCROLL ================= */
.background-decor.animate .flower-top-left { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: sway 12s ease-in-out infinite alternate, flowerEnterLeft 1s ease forwards; 
}

.background-decor.animate .flower-top-right { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: swayReverse 14s ease-in-out infinite alternate, flowerEnterRight 1s ease forwards; 
}

.background-decor.animate .flower-bottom-left { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: sway 16s ease-in-out infinite alternate, flowerEnterBottomLeft 1s ease forwards; 
}

.background-decor.animate .flower-bottom-right { 
  opacity: 1; 
  transform: translate(0,0) rotate(0deg); 
  animation: swayReverse 18s ease-in-out infinite alternate, flowerEnterBottomRight 1s ease forwards; 
}

.background-decor.animate .flower-bottom-center { 
  opacity: 1; 
  transform: translateY(0); 
  animation: sway 20s ease-in-out infinite alternate, flowerEnterCenter 1s ease forwards; 
}
.flower {
  opacity: 0;
  transform: translateY(50px) rotate(0deg);
  transition: all 1s ease-out;
}

.background-decor.animate .flower {
  opacity: 1;
  transform: translateY(0) rotate(0deg);
  animation: sway 12s ease-in-out infinite alternate;
}


/* ================= KEYFRAMES MASUK SESUAI ARAH ================= */
@keyframes flowerEnterLeft {
  0% { transform: translate(-60px, -20px) rotate(-5deg); }
  100% { transform: translate(0, 0) rotate(0deg); }
}

@keyframes flowerEnterRight {
  0% { transform: translate(60px, -20px) rotate(5deg); }
  100% { transform: translate(0, 0) rotate(0deg); }
}

@keyframes flowerEnterBottomLeft {
  0% { transform: translate(-50px, 50px) rotate(-5deg); }
  100% { transform: translate(0, 0) rotate(0deg); }
}

@keyframes flowerEnterBottomRight {
  0% { transform: translate(50px, 50px) rotate(5deg); }
  100% { transform: translate(0, 0) rotate(0deg); }
}

@keyframes flowerEnterCenter {
  0% { transform: translateY(60px); }
  100% { transform: translateY(0); }
}

/* ================= KEYFRAMES GOYANG ================= */
@keyframes sway {
  0% { transform: rotate(-1.5deg); }
  50% { transform: rotate(1.5deg); }
  100% { transform: rotate(-1.5deg); }
}

@keyframes swayReverse {
  0% { transform: rotate(1.5deg); }
  50% { transform: rotate(-1.5deg); }
  100% { transform: rotate(1.5deg); }
}

/* ================= KEYFRAMES RUMAH ================= */
@keyframes houseUp {
  0% { opacity: 0; transform: translateX(-50%) translateY(70px); }
  100% { opacity: 1; transform: translateX(-50%) translateY(0); }
}
</style>
