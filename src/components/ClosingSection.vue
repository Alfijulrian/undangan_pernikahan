<template>
  <section class="section closing-section">
    <div class="content-wrapper">
      <!-- Bingkai atas -->
      <div class="decorative-border top animated"></div>

      <p class="animated">
        Merupakan suatu kehormatan dan kebahagiaan bagi kami
        apabila Bapak/Ibu/Saudara/i berkenan hadir.
      </p>
      <h3 class="animated">Aldes & Suci</h3>

      <!-- Bingkai bawah -->
      <div class="decorative-border bottom animated"></div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'

// Animasi muncul saat scroll
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
</script>

<style scoped>
.section.closing-section {
  padding: 60px 20px;
  background: #fdf6f0;
  text-align: center;
}

.content-wrapper {
  max-width: 600px;
  margin: 0 auto;
}

p {
  font-size: 16px;
  line-height: 1.8;
  color: #333;
  margin: 20px 0;
  opacity: 0;
  transform: translateY(20px);
}

h3 {
  font-family: 'Great Vibes', cursive;
  font-size: 36px;
  color: #ff6b6b;
  margin-bottom: 40px;
  opacity: 0;
  transform: translateY(20px);
}

/* Bingkai dekoratif */
.decorative-border {
  width: 150px;
  height: 4px;
  background: linear-gradient(90deg, #ff6b6b, #ffb86c);
  border-radius: 2px;
  margin: 10px auto;
  opacity: 0;
  transform: translateY(20px);
}

/* Jika bingkai atas sedikit ke bawah */
.decorative-border.top {
  margin-bottom: 20px;
}

/* Jika bingkai bawah sedikit ke atas */
.decorative-border.bottom {
  margin-top: 20px;
}

/* Animasi Fade In Up */
@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fadeInUp {
  animation: fadeInUp 0.8s ease-out forwards;
}

/* Delay animasi */
.decorative-border.top.fadeInUp { animation-delay: 0s; }
p.fadeInUp { animation-delay: 0.2s; }
h3.fadeInUp { animation-delay: 0.4s; }
.decorative-border.bottom.fadeInUp { animation-delay: 0.6s; }
</style>
