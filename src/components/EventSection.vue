<template>
  <section class="section">
    <!-- Background dekorasi -->
    <BackgroundDecor />

    <!-- Konten Event di atas BackgroundDecor -->
    <div class="content-wrapper">
      <h2>Detail Acara</h2>

      <div class="card">
        <h3>Akad Nikah</h3>
        <p>Rabu, 07 Januari 2026</p>
        <p>09.00 WIB</p>
        <p>Kediaman Mempelai Wanita</p>
      </div>

      <div class="card">
        <h3>Resepsi</h3>
        <p>Kamis, 08 Januari 2026</p>
        <p>11.00 WIB</p>
        <p>Bertempat di Kediaman Wanita</p>
      </div>
    </div>
  </section>
</template>

<script setup>
import BackgroundDecor from './BackgroundDecor.vue'
</script>

<style scoped>
.section {
  position: relative;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 30px 15px;
  overflow: hidden;
}

/* Wrapper konten agar muncul di atas BackgroundDecor */
.content-wrapper {
  position: relative;
  z-index: 10; /* Pastikan konten di atas dekorasi */
  text-align: center;
  width: 100%;
  max-width: 400px;
}

/* Judul */
h2 {
  font-family: 'Times New Roman', serif;
  font-size: 28px;
  color: #ff69b4;
  margin-bottom: 30px;
}

/* Kartu acara */
.card {
  background-color: rgba(255, 255, 255, 0.85);
  padding: 15px;
  border-radius: 12px;
  margin-bottom: 20px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}

.card h3 {
  font-size: 18px;
  font-weight: bold;
  color: #333;
  margin-bottom: 8px;
}

.card p {
  font-size: 14px;
  color: #555;
  margin: 4px 0;
}

/* Responsif untuk mobile */
@media (max-width: 768px) {
  h2 { font-size: 24px; }
  .card { padding: 12px; }
}
</style>
