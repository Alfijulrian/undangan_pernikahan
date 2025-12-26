<template>
  <section class="section gallery-section">
    <h2>Galeri</h2>
    
    <div class="gallery-container"> 
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
  '/images/f_cowok.jpg',
  '/images/f_cewek.jpg',
  '/images/BNK_9140.jpg',
  '/images/BNK_9142 (1).jpg',
  '/images/BNK_9148.jpg',
  '/images/BNK_9150.jpg',
  '/images/BNK_9241.jpg',
  '/images/BNK_9319.jpg',
  '/images/BNK_9336.jpg',
  '/images/BNK_9355.jpg',
  '/images/BNK_9357.jpg',
  '/images/BNK_9369.jpg'
]

const galleryRefs = ref([])

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

/* Scroll container */
.gallery-container {
  width: 100%;
  overflow-x: auto;
  padding-bottom: 1rem;
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.gallery-container::-webkit-scrollbar {
  display: none;
}

/* Flex horizontal */
.gallery {
  display: flex;
  gap: 10px; 
  width: max-content; 
}

/* Gallery item */
.gallery-item {
  flex-shrink: 0; 
  width: calc(50vw - 10px); /* default HP: 2 item */
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
  height: auto; /* otomatis menyesuaikan tinggi */
  display: block;
  object-fit: cover;
  border-radius: 12px;
  transition: transform 0.3s ease;
}

.gallery-item img:hover {
  transform: scale(1.05);
}

/* Tablet: 3 item */
@media (min-width: 600px) {
  .gallery-item {
    width: calc(33.33vw - 12px);
  }
}

/* Desktop: 4 item */
@media (min-width: 992px) {
  .gallery-item {
    width: calc(25vw - 12px);
  }
}
</style>
