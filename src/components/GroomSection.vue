<template>
  <section class="groom-profile">
    <!-- Background dekoratif -->
    <BackgroundDecor />

    <!-- Card Profil Pengantin Laki-laki -->
    <div ref="profileCard" :class="['profile-card', { visible: isVisible }]">
      <!-- Foto menyesuaikan bingkai -->
      <img src="/images/f_cowok.jpg" alt="Aldes Fitra Ramadhan" class="photo" />

      <!-- Nama -->
      <h2 class="name">Aldes Fitra Ramadhan</h2>

      <!-- Nama Orang Tua -->
      <p class="parents">Putra dari Bapak Ali Akbar & Muatmainnah</p>

      <!-- Instagram -->
      <a href="https://www.instagram.com/aldes_fitra_ramadhan?igsh=MXdtaTBkdHFheTlmYQ==" target="_blank" class="ig">
        <i class="fa-brands fa-instagram"></i> instagram
      </a>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import BackgroundDecor from './BackgroundDecor.vue'

const profileCard = ref(null)
const isVisible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        isVisible.value = true
        observer.unobserve(profileCard.value) // hentikan observasi setelah terlihat
      }
    },
    { threshold: 0.3 } // animasi jalan saat 30% terlihat
  )
  observer.observe(profileCard.value)
})
</script>

<style scoped>
/* ================= GROOM PROFILE ================= */
.groom-profile {
  position: relative;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  z-index: 1;
  padding: 20px;
}

/* ================= PROFILE CARD ================= */
.profile-card {
  background: rgba(255, 182, 193, 0.25);
  border: 2px solid rgba(255, 192, 203, 0.4);
  border-radius: 50px 50px 15px 15px;
  padding: 40px 20px 25px 20px;
  max-width: 280px;
  width: 100%;
  text-align: center;
  backdrop-filter: blur(6px);
  box-shadow: 0 8px 20px rgba(255, 105, 180, 0.3);
  color: white;

  /* state awal animasi */
  opacity: 0;
  transform: translateY(30px);
  transition: all 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}

.profile-card.visible {
  opacity: 1;
  transform: translateY(0);
}

/* ================= FOTO ================= */
.photo {
  width: 100%;
  height: auto;
  object-fit: cover;
  border-radius: 30px 30px 0 0;
  margin-bottom: 1rem;

  /* animasi masuk */
  opacity: 0;
  transform: translateY(-20px);
  transition: all 0.8s ease-out 0.2s;
}

.profile-card.visible .photo {
  opacity: 1;
  transform: translateY(0);
}

/* ================= TEKS ================= */
.name,
.parents,
.ig {
  opacity: 0;
  transform: translateY(20px);
  transition: all 0.8s ease-out;
}

.profile-card.visible .name {
  opacity: 1;
  transform: translateY(0);
  transition-delay: 0.4s;
}

.profile-card.visible .parents {
  opacity: 1;
  transform: translateY(0);
  transition-delay: 0.6s;
}

.profile-card.visible .ig {
  opacity: 1;
  transform: translateY(0);
  transition-delay: 0.8s;
}

/* ================= NAMA ================= */
.name {
  font-size: 1.5rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

/* ================= NAMA ORANG TUA ================= */
.parents {
  font-size: 1rem;
  margin-bottom: 0.5rem;
}

/* ================= INSTAGRAM ================= */
.ig {
  font-size: 0.95rem;
  color: #fff;
  text-decoration: underline;
  font-weight: 600;
  display: inline-flex;
  align-items: center;
  justify-content: center;
}

.ig i {
  margin-right: 6px;
}

/* ================= RESPONSIVE MOBILE ================= */
@media (max-width: 480px) {
  .profile-card {
    max-width: 220px;
    padding: 30px 15px 20px 15px;
  }

  .photo {
    width: 100%;
    height: auto;
  }

  .name {
    font-size: 1.2rem;
  }

  .parents {
    font-size: 0.9rem;
  }

  .ig {
    font-size: 0.85rem;
  }
}
</style>
