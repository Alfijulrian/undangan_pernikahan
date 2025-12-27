<template>
  <section class="section gallery-section">
    <h2>Galeri</h2>

    <div class="gallery-container" ref="galleryContainer">
      <div class="gallery">
        <div 
          class="gallery-item" 
          v-for="(img, index) in images" 
          :key="index" 
          :ref="el => galleryRefs[index] = el"
        >
          <img :src="img" alt="Foto Pernikahan">
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const images = [
  '/images/f1.webp',
  '/images/f2.webp',
  '/images/f3.webp',
  '/images/f4.webp',
  '/images/f5.webp',
  '/images/f6.webp'
]

const galleryRefs = ref([])
const galleryContainer = ref(null)

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('show')
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.1 } 
  )
  galleryRefs.value.forEach(el => {
    if (el) observer.observe(el)
  })
})
</script>

<style scoped>
.gallery-section {
  text-align: center;
  padding: 2rem 1rem;
  background-color: #ffe6f0;
}

h2 {
  margin-bottom: 1.5rem;
  color: #ff69b4;
  font-size: 1.8rem;
}

/* Container utama */
.gallery-container {
  width: 100%;
}

/* Grid responsive */
.gallery {
  display: grid;
  gap: 15px;
  grid-template-columns: 1fr; /* Mobile: 1 kolom full lebar */
}

/* Item gallery */
.gallery-item {
  width: 100%;
  border-radius: 12px;
  overflow: hidden;
  transform: scale(0.8);
  opacity: 0;
  transition: transform 0.6s ease, opacity 0.6s ease;
}

.gallery-item.show {
  transform: scale(1);
  opacity: 1;
}

.gallery-item img {
  width: 100%;
  height: auto;
  display: block;
  object-fit: cover;
  border-radius: 12px;
  transition: transform 0.3s ease;
}

.gallery-item img:hover {
  transform: scale(1.05);
}

/* Tablet: 2 kolom */
@media (min-width: 600px) {
  .gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Desktop: 3 kolom */
@media (min-width: 992px) {
  .gallery {
    grid-template-columns: repeat(3, 1fr);
  }
}

/* Large Desktop: 4 kolom */
@media (min-width: 1200px) {
  .gallery {
    grid-template-columns: repeat(4, 1fr);
  }
}
</style>
