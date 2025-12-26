<template>
  <section class="opening">
    <!-- Bingkai atas -->
    <img 
      ref="frameTop" 
      src="/images/bingkai_atas.png" 
      alt="Bingkai Atas" 
      class="frame frame-top animated" 
    />

    <!-- Bismillah / Ayat pembuka -->
    <p ref="arabText" class="arab animated">
      بِسْمِ اللهِ الرَّحْمٰنِ الرَّحِيْمِ
    </p>

    <!-- Kata-kata pemanis undangan -->
    <p ref="mainText" class="text animated">
      Dengan memohon rahmat dan ridho Allah SWT,<br />
      kami mengundang Bapak/Ibu/Saudara/i untuk hadir dalam acara pernikahan putra dan putri kami.<br />
      Semoga pernikahan ini menjadi awal keluarga yang sakinah, mawaddah, dan rahmah, serta selalu berada dalam lindungan Allah SWT.
    </p>

    <!-- Hadis pemanis -->
    <p ref="hadisText" class="hadis animated">
      “Nikah adalah sunnahku, siapa yang meninggalkannya bukan dari golonganku.”<br />
      <span>(HR. Bukhari dan Muslim)</span>
    </p>

    <!-- Bingkai bawah -->
    <img 
      ref="frameBottom" 
      src="/images/bingkai_bawah.png" 
      alt="Bingkai Bawah" 
      class="frame frame-bottom animated" 
    />
  </section>
</template>

<script setup>
import { onMounted } from 'vue'

// Animasi fadeInUp saat scroll
onMounted(() => {
  const animatedElements = document.querySelectorAll('.animated')
  const observerOptions = { root: null, rootMargin: '0px', threshold: 0.1 }

  const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.classList.add('fadeInUp')
        observer.unobserve(entry.target)
      }
    })
  }, observerOptions)

  animatedElements.forEach(el => observer.observe(el))
})

// Musik otomatis saat buka undangan
document.addEventListener('startMusic', async () => {
  if (!window.bgMusic) {
    window.bgMusic = new Audio('/music/wedding-music.mp3') // ganti path musik
    window.bgMusic.loop = true
  }
  if (window.bgMusic.paused) {
    await window.bgMusic.play()
  }
})
</script>

<style scoped>
.opening {
  position: relative;
  text-align: center;
  padding: 40px 20px;
  background: #fdf6f0;
}

.frame {
  width: 100px;
  max-width: 150px;
  margin: 20px auto;
  display: block;
}

.arab {
  font-size: 24px;
  font-family: 'Scheherazade', serif;
  margin: 15px 0;
  color: #333;
}

.text {
  font-size: 16px;
  line-height: 1.7;
  margin: 15px 0;
  color: #444;
}

.hadis {
  font-size: 14px;
  font-style: italic;
  color: #666;
  margin: 15px 0 30px 0;
}

.hadis span {
  display: block;
  font-size: 12px;
  margin-top: 5px;
  color: #888;
}

/* =============================
   Animasi Fade In Up
   ============================= */
@keyframes fadeInUp {
  to { opacity: 1; transform: translateY(0); }
}

.animated {
  opacity: 0;
  transform: translateY(20px);
}

.fadeInUp {
  animation: fadeInUp 0.8s ease-out forwards;
}

/* Delay animasi untuk tiap elemen */
.frame-top.fadeInUp { animation-delay: 0s; }
.arab.fadeInUp { animation-delay: 0.2s; }
.text.fadeInUp { animation-delay: 0.4s; }
.hadis.fadeInUp { animation-delay: 0.6s; }
.frame-bottom.fadeInUp { animation-delay: 0.8s; }
</style>
