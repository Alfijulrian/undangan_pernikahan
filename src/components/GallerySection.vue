<template>
  <section class="gallery-section">
    <h2>Galeri Foto</h2>
    <div class="gallery">
      <div
        class="gallery-item"
        v-for="(img, index) in images"
        :key="index"
        :ref="el => galleryRefs[index] = el"
        :class="{ 'is-visible': visible[index] }"
      >
        <img :src="img" alt="Foto Pernikahan" />
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
  '/images/f6.webp',
]

const galleryRefs = ref([])
const visible = ref(Array(images.length).fill(false))

onMounted(() => {
  const observer = new IntersectionObserver(
    entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const index = galleryRefs.value.indexOf(entry.target)
          if (index !== -1) visible.value[index] = true
          observer.unobserve(entry.target)
        }
      })
    },
    { threshold: 0.2 }
  )

  galleryRefs.value.forEach(el => {
    if (el) observer.observe(el)
  })
})
</script>

<style scoped>
.gallery-section {
  padding: 3rem 2rem;
  text-align: center;
  max-width: 1400px;
  margin: 0 auto;
}

.gallery-section h2 {
  font-size: 2.5rem;
  margin-bottom: 2.5rem;
  color: #333;
  font-family: 'Segoe UI', sans-serif;
}

.gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  justify-items: center;
  width: 100%;
}

/* Gallery Item */
.gallery-item {
  width: 100%;
  aspect-ratio: 9 / 16;
  overflow: hidden;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.2);
  transform: translateY(30px);
  opacity: 0;
  transition: transform 0.6s ease, opacity 0.6s ease, transform 0.3s ease;
}

/* Fade-in saat muncul */
.gallery-item.is-visible {
  transform: translateY(0);
  opacity: 1;
}

/* Zoom saat hover */
.gallery-item:hover {
  transform: scale(1.08);
  box-shadow: 0 14px 35px rgba(0,0,0,0.3);
}

.gallery-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
}
</style>
