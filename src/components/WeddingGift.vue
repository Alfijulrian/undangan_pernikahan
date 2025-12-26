<template>
  <section class="section wedding-gift" id="wedding-gift">
    <!-- Background dekoratif -->
    <BackgroundDecor />

    <div class="content-wrapper">
      <h2 class="animated">Wedding Gift</h2>
      <p class="animated">Bagi yang ingin memberikan hadiah, dapat melalui rekening berikut:</p>

      <!-- Kotak BRI -->
      <div class="gift-box animated">
        <div class="bank-header">
          <img src="/images/bri.png" alt="BRI" class="bank-icon" />
          <h3>BRI</h3>
        </div>
        <p class="account-number">028401048554502</p>
        <button @click="copyRekening('028401048554502')">Salin Nomor</button>
      </div>

      <!-- Kotak Dana -->
      <div class="gift-box animated">
        <div class="bank-header">
          <img src="/images/dana.jpg" alt="Dana" class="bank-icon" />
          <h3>Dana</h3>
        </div>
        <p class="account-number">085271981372</p>
        <button @click="copyRekening('085271981372')">Salin Nomor</button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'
import BackgroundDecor from './BackgroundDecor.vue'

const copyRekening = (noRek) => {
  navigator.clipboard.writeText(noRek).then(() => {
    alert(`Nomor ${noRek} berhasil disalin!`)
  })
}

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
.section.wedding-gift {
  position: relative;
  padding: 60px 20px;
  text-align: center;
  min-height: 100vh;
  overflow: hidden;
}

/* Konten wrapper agar di atas background */
.content-wrapper {
  position: relative;
  z-index: 10;
  max-width: 500px;
  margin: 0 auto;
  color: #fff; /* Warna teks agar terbaca di atas background */
}

h2 {
  font-size: 36px;
  margin-bottom: 20px;
  opacity: 0;
  transform: translateY(20px);
}

p {
  font-size: 16px;
  margin-bottom: 30px;
  opacity: 0;
  transform: translateY(20px);
}

/* Kotak Gift */
.gift-box {
  border: 2px solid #ff6b6b;
  border-radius: 12px;
  padding: 20px;
  margin-bottom: 25px;
  background: rgba(255,248,245,0.9);
  opacity: 0;
  transform: translateY(40px);
  transition: transform 0.3s, box-shadow 0.3s;
}

.bank-header {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  margin-bottom: 10px;
}

.bank-header h3 {
  font-size: 20px;
  color: #ff6b6b;
  margin: 0;
}

.bank-icon {
  width: 32px;
  height: 32px;
  object-fit: contain;
}

.gift-box .account-number {
  font-size: 18px;
  font-weight: bold;
  color: #000; 
  margin-bottom: 10px;
}

button {
  padding: 8px 16px;
  background: #ff6b6b;
  color: #fff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: transform 0.2s, background 0.2s;
}

button:hover {
  transform: scale(1.05);
  background: #ff4c4c;
}

/* Animasi Fade In Up */
@keyframes fadeInUp {
  to { opacity: 1; transform: translateY(0); }
}
.fadeInUp {
  animation: fadeInUp 0.8s ease-out forwards;
}
h2.fadeInUp { animation-delay: 0s; }
p.fadeInUp { animation-delay: 0.2s; }
.gift-box:nth-child(3).fadeInUp { animation-delay: 0.4s; }
.gift-box:nth-child(4).fadeInUp { animation-delay: 0.6s; }
</style>
