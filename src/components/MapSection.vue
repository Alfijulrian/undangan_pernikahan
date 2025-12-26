<template>
  <section class="section dark location-section">
    <h2>Lokasi Acara</h2>
    <div class="map-container">
      <iframe 
  src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3952.12345!2d102.609176!3d-0.402498!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0xabcdef1234567890!2sKediaman%20Wanita!5e0!3m2!1sid!2sid!4v1700000000000" 
  width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy">
        </iframe>
    </div>
    <a 
      href="https://maps.app.goo.gl/Hh95f5ELkSh8o1Q47" 
      target="_blank" 
      class="btn-maps"
    >
      Buka di Google Maps
    </a>
  </section>
</template>
<script setup>
// Tidak perlu JS tambahan, link langsung ke Google Maps
</script>

<style scoped>
.section.dark {
  background: #ff94cf;
  color: #fff;
  padding: 3rem 1.5rem;
  text-align: center;
}

.location-section h2 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
  font-family: 'Segoe UI', sans-serif;
}

.map-container {
  width: 100%;
  max-width: 800px;
  height: 350px;
  margin: 0 auto 1.5rem auto;
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.3);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.map-container:hover {
  transform: scale(1.02);
  box-shadow: 0 15px 40px rgba(0, 0, 0, 0.4);
}

.map-container iframe {
  width: 100%;
  height: 100%;
  border: 0;
}

.btn-maps {
  display: inline-block;
  padding: 0.8rem 2rem;
  background: #398b3d;
  color: #fff;
  font-weight: bold;
  border-radius: 12px;
  text-decoration: none;
  transition: background 0.3s ease, transform 0.3s ease;
}

.btn-maps:hover {
  background: #ff4c4c;
  transform: scale(1.05);
}
</style>
