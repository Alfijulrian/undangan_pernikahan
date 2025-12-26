<template>
  <section class="section gallery-section">
    <h2>Galeri</h2>
    
    <div class="gallery-wrapper">
      <!-- Panah kiri -->
      <button class="scroll-btn left" @click="scrollLeft">‹</button>

      <!-- Scroll container -->
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

      <!-- Panah kanan -->
      <button class="scroll-btn right" @click="scrollRight">›</button>
    </div>
    
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const images = [
  '/images/f_cowok.jpg',
  '/images/f_cewek.jpg',
  '/images/BNK_9140.jpg',
  '/images/f1.webp',
  '/images/f2.webp',
  '/images/f3.webp',
  '/images/f4.webp',
  '/images/f5.webp',
  '/images/f6.webp',
  '/images/BNK_9150.jpg',
  '/images/BNK_9241.jpg',
  '/images/BNK_9319.jpg',
  '/images/BNK_9336.jpg',
  '/images/BNK_9355.jpg',
  '/images/BNK_9357.jpg',
  '/images/BNK_9369.jpg'
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

// Fungsi scroll
const scrollLeft = () => {
  galleryContainer.value.scrollBy({ left: -200, behavior: 'smooth' })
}
const scrollRight = () => {
  galleryContainer.value.scrollBy({ left: 200, behavior: 'smooth' })
}
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

.gallery-wrapper {
  position: relative;
  width: 100%;
}

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

.gallery {
  display: flex;
  gap: 10px; 
  width: max-content; 
}

.gallery-item {
  flex-shrink: 0; 
  width: calc(50vw - 10px);
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

/* Scroll buttons */
.scroll-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 35px;
  height: 60px;
  background: rgba(255,255,255,0.7);
  border: none;
  font-size: 30px;
  font-weight: bold;
  cursor: pointer;
  border-radius: 6px;
  z-index: 10;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: background 0.3s;
}

.scroll-btn:hover {
  background: rgba(255,255,255,1);
}

.scroll-btn.left {
  left: 5px;
}

.scroll-btn.right {
  right: 5px;
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
