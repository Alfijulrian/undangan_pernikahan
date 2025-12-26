<script setup>
/* ================= IMPORT SEMUA KOMPONEN ================= */
import HeroSection from './components/HeroSection.vue'
import OpeningSection from './components/OpeningSection.vue'
import GroomSection from './components/GroomSection.vue'
import BrideSection from './components/BrideSection.vue'
import EventSection from './components/EventSection.vue'
import CountdownSection from './components/CountdownSection.vue'
import GallerySection from './components/GallerySection.vue'
import MapSection from './components/MapSection.vue'
import WeddingGift from './components/WeddingGift.vue'
import ClosingSection from './components/ClosingSection.vue'
import MusicPlayer from './components/MusicPlayer.vue' // Komponen musik

/* ================= FUNGSI BUKA UNDANGAN ================= */
const openInvitation = () => {
  const opening = document.getElementById('opening-section')
  if (opening) opening.scrollIntoView({ behavior: 'smooth' })

  // Trigger musik agar otomatis play
  document.dispatchEvent(new Event('startMusic'))
}
</script>

<template>
  <div id="app">
    <!-- ================= MUSIC PLAYER ================= -->
    <MusicPlayer />

    <!-- ================= HERO SECTION ================= -->
    <HeroSection>
      <!-- Slot Tombol Buka Undangan -->
      <template #button>
        <button class="open-btn" @click="openInvitation">
          Buka Undangan
        </button>
      </template>
    </HeroSection>

    <!-- ================= OPENING / PEMANIS ================= -->
    <OpeningSection id="opening-section" />

    <!-- ================= PENGANTIN ================= -->
    <GroomSection />
    <BrideSection />

    <!-- ================= DETAIL ACARA ================= -->
    <EventSection />

    <!-- ================= COUNTDOWN ================= -->
    <CountdownSection />

    <!-- ================= GALLERY ================= -->
    <GallerySection />

    <!-- ================= MAP ================= -->
    <MapSection />

    <!-- ================= WEDDING GIFT ================= -->
    <WeddingGift />

    <!-- ================= CLOSING ================= -->
    <ClosingSection />
  </div>
</template>

<style>
/* ================= RESET DASAR ================= */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body, html, #app {
  font-family: 'Poppins', sans-serif;
  width: 100%;
  min-height: 100%;
  background: #fdf6f0;
  color: #333;
  overflow-x: hidden;
}

/* ================= SCROLL SMOOTH ================= */
html {
  scroll-behavior: smooth;
}

/* ================= GLOBAL SECTION ================= */
section {
  position: relative;
  width: 100%;
  padding: 4rem 2rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

/* Background section image jika dibutuhkan */
section .bg-photo {
  position: absolute;
  inset: 0;
  background-size: cover;
  background-position: center;
  z-index: -1;
  filter: brightness(0.6);
}

/* ================= TOMBOL BUKA UNDANGAN ================= */
.open-btn {
  padding: 12px 28px;
  font-size: 18px;
  font-weight: bold;
  border: none;
  border-radius: 12px;
  background: #ff6b6b;
  color: #fff;
  cursor: pointer;
  transition: transform 0.2s, background 0.2s;
  margin-top: 20px;
}

.open-btn:hover {
  background: #ff4c4c;
  transform: scale(1.05);
}
</style>
