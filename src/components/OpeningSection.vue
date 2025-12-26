<template>
  <!-- Section Opening -->
  <section class="opening-section">
    <!-- Bingkai / gambar atas -->
    <img src="/images/bingkai_atas.png" alt="Bingkai Atas" class="frame top-frame" />

    <!-- Tulisan Bismillah -->
    <h2 class="bismillah">بسم الله الرحمن الرحيم</h2>

    <!-- Tulisan Assalamu’alaikum dalam Arab -->
    

    <!-- Kata-kata pembuka panjang -->
    <p class="opening-text">
      Dengan memohon rahmat dan ridho Allah SWT, kami mengundang Bapak/Ibu/Saudara/i 
      untuk hadir dan memberikan doa restu pada acara pernikahan kami. Semoga kehadiran 
      Anda menjadi bagian dari kebahagiaan dan keberkahan dalam pernikahan kami. 
      Mohon doa, restu, dan keikhlasan untuk menyaksikan awal perjalanan hidup kami 
      yang penuh berkah, cinta, dan kasih sayang. Semoga Allah SWT senantiasa melimpahkan 
      rahmat, keberkahan, dan kebahagiaan pada keluarga kita semua.
    </p>

    <!-- Bingkai / gambar bawah -->
    <img src="/images/bingkai_bawah.png" alt="Bingkai Bawah" class="frame bottom-frame" />
  </section>
</template>

<script setup>
// Tidak ada script karena halaman ini statis
</script>

<style scoped>
/* Opening Section */
.opening-section {
  position: relative;
  min-height: 100vh;
  padding: 60px 20px;
  text-align: center;
  background-color: #fff0f5;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

/* Bingkai / Frame */
.frame {
  max-width: 90%;
  height: auto;
  margin: 20px 0;
}

.top-frame {
  margin-bottom: 40px;
}

.bottom-frame {
  margin-top: 40px;
}

/* Tulisan Bismillah */
.bismillah {
  font-family: 'Scheherazade', serif;
  font-size: 36px;
  color: #ff69b4;
  margin-bottom: 10px;
}

/* Tulisan Assalamu’alaikum Arab */
.arabic-greeting {
  font-family: 'Scheherazade', serif;
  font-size: 28px;
  color: #d6336c;
  margin-bottom: 20px;
}

/* Kata-kata pembuka panjang */
.opening-text {
  font-size: 16px;
  color: #333;
  max-width: 380px;
  line-height: 1.8;
  margin: 0 auto;
}

/* Responsif Mobile */
@media (max-width: 768px) {
  .bismillah {
    font-size: 28px;
  }

  .arabic-greeting {
    font-size: 22px;
  }

  .opening-text {
    font-size: 14px;
    max-width: 90%;
  }
}
</style>
