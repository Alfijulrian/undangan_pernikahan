<template>
  <section class="section" id="detail-acara-section">
    <div class="background-overlay"></div>
    
    <div class="content-wrapper">
      <h2 class="animated">Detail Acara</h2> 

      <div class="card animated"> 
        <h3>Akad Nikah</h3>
        <p>rabu, 07 Januari 2026</p>
        <p>09.00 WIB</p>
        <p>Kediaman Mempelai Wanita</p>
      </div>

      <div class="card animated"> 
        <h3>Resepsi</h3>
        <p>kamis, 08 Januari 2026</p>
        <p>11.00 WIB</p>
        <p>Bertempat kediaman wanita</p>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* 1. Pengaturan Latar Belakang Penuh */
.section {
  /* Mengatur gambar sebagai latar belakang */
  background-image: url('/images/BNK_9336.jpg');
  background-size: cover;
  background-position: center;
  background-attachment: fixed;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  padding: 40px 20px;
}

/* 2. Overlay untuk Keterbacaan */
.background-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  /* Tambahkan warna gelap/transparan agar teks putih lebih menonjol */
  background-color: rgba(0, 0, 0, 0.4); 
}

/* 3. Wrapper Konten (memastikan konten di atas overlay) */
.content-wrapper {
  position: relative;
  z-index: 1;
  text-align: center;
  max-width: 400px;
  width: 100%;
}

/* 4. Gaya Judul */
h2 {
  font-family: 'Times New Roman', serif;
  font-size: 40px;
  color: #fffc4e;
  margin-bottom: 40px;
  /* Tambahan untuk inisialisasi animasi pada h2 */
  opacity: 0; 
  transform: translate3d(0, 20px, 0); /* Mulai lebih dekat ke posisi akhir */
}

/* 5. Gaya Kartu Detail Acara */
.card {
  padding: 20px;
  border-radius: 12px;
  margin-bottom: 25px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  
  /* Tambahan untuk inisialisasi animasi pada card */
  opacity: 0;
  transform: translate3d(0, 40px, 0); /* Mulai 40px di bawah posisi akhir */
  transition: none; /* Nonaktifkan transisi awal */
}

.card h3 {
  font-size: 20px;
  font-weight: bold;
  color: #000000;
  margin-bottom: 10px;
}

.card p {
  font-size: 16px;
  color: #000000;
  margin: 5px 0;
}

/* =============================
   6. Keyframes dan Animasi 
   ============================= */

/* Definisikan keyframes untuk efek Fade In Up */
@keyframes fadeInUp {
  to {
    opacity: 1;
    transform: translate3d(0, 0, 0);
  }
}

/* Class yang ditambahkan oleh JavaScript ketika elemen masuk ke viewport */
.fadeInUp {
  opacity: 0; /* Override: Mulai dari opacity 0 */
  animation: fadeInUp 0.8s ease-out forwards;
}

/* Atur durasi delay untuk setiap elemen agar muncul bergantian */
h2.fadeInUp {
  animation-delay: 0s;
}

.card:nth-child(2).fadeInUp { /* Kartu Akad Nikah */
  animation-delay: 0.2s; 
}

.card:nth-child(3).fadeInUp { /* Kartu Resepsi */
  animation-delay: 0.5s; 
}
</style>

<script>
document.addEventListener('DOMContentLoaded', (event) => {
    // 1. Pilih semua elemen yang memiliki class 'animated'
    const animatedElements = document.querySelectorAll('.animated');

    // 2. Definisikan opsi observer
    const observerOptions = {
        root: null, // Mengamati relatif terhadap viewport
        rootMargin: '0px',
        threshold: 0.1 // Pemicu saat 10% elemen terlihat
    };

    // 3. Buat observer
    const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
            // Jika elemen terlihat (intersecting)
            if (entry.isIntersecting) {
                // Tambahkan class untuk memulai animasi
                entry.target.classList.add('fadeInUp');
                // Hentikan pengamatan setelah dianimasikan
                observer.unobserve(entry.target);
            }
        });
    }, observerOptions);

    // 4. Mulai mengamati setiap elemen
    animatedElements.forEach(element => {
        observer.observe(element);
    });
});
</script>