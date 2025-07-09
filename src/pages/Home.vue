<template>
  <!-- Slide-down overlay with centered CULSE -->
  <div v-if="showOverlay" class="slide-overlay">
    <img src="/images/Culse.jpg" alt="CULSE Logo" class="overlay-image" />

  </div>

   <!-- 🔽 Add video here -->
   <video autoplay muted loop playsinline class="video-background">
    <source src="/videos/background-video.mp4" type="video/mp4" />
  </video>
  
  <!-- Hero section -->
  <div class="hero">
    <div class="tagline">CREATING</div>
    <div class="headline">THE UNTHINKABLE</div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const showOverlay = ref(true)

onMounted(() => {
  setTimeout(() => {
    showOverlay.value = false
  }, 2500) // total duration = 1s pause + 1.5s slide
})
</script>

<style scoped>
/* ------------ Slide-down overlay ------------ */
.slide-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background: black;
  z-index: 9999;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: holdAndSlide 2.5s forwards;
}

@keyframes holdAndSlide {
  0%   { transform: translateY(0); }
  40%  { transform: translateY(0); }     /* Hold for 1s */
  100% { transform: translateY(100%); }  /* Slide down */
}

.overlay-text {
  color: white;
  font-size: 3rem;
  font-family: 'Rework Bold', sans-serif;
  letter-spacing: 3px;
  text-transform: uppercase;
}

/* ------------ Hero section ------------ */
.hero {
  position: absolute;
  top: 80%;
  left: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
  color: white;
  z-index: 1;
  padding: 0 2rem;
  white-space: nowrap;
}

.tagline {
  font-family: 'Rework Semibold', sans-serif;
  font-size: 1.25rem;
  font-weight: 600;
  letter-spacing: 2px;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
}

.headline {
  font-family: 'Rework Bold', sans-serif;
  font-size: 6rem;
  font-weight: 700;
  text-transform: uppercase;
  line-height: 1;
}

@media (max-width: 768px) {
  .headline { font-size: 2.2rem; }
  .tagline  { font-size: 0.7rem; }
}
.overlay-image {
  max-width: 300px;
  width: 80%;
  height: auto;
  z-index: 99999;
  animation: fadeIn 1.5s ease-in-out;
}
@keyframes fadeIn {
  from { opacity: 0; transform: scale(0.95); }
  to { opacity: 1; transform: scale(1); }
}

</style>
