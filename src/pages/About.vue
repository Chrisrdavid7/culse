<template>
  <Navbar />

  <div class="about-content">
    <div class="slide-overlay" v-if="showOverlay">
   
    </div>

    <div class="about-hero">
      <div class="overlay"></div>
      <div class="about-text">ABOUT</div>
    </div>

    <div class="about-quote-row">
      <div class="quote-author-left">CULSE</div>
      <div class="quote-body">
        <p>
          Creativity isn’t just about being different — it’s about being honest.
          It’s about crafting something that feels bold yet familiar, sharp yet
          comforting. Something that reflects your experience, your values, and
          your voice in a way that’s both powerful and deeply human.
          <br /><br />
          A mixture of heart and culture.
        </p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Navbar from '../components/Navbar.vue'

const showOverlay = ref(true)

onMounted(() => {
  setTimeout(() => {
    showOverlay.value = false
  }, 2500)
})
</script>

<style scoped>
.about-content {
  position: relative;
  z-index: 1;
}

.slide-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: black;
  z-index: 9999;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: slideDown 2.5s ease forwards;
}

.overlay-text {
  color: white;
  font-size: 3rem;
  font-family: 'Rework Display Regular', sans-serif;
  letter-spacing: 0.2rem;
  text-transform: uppercase;
}

@keyframes slideDown {
  0% { transform: translateY(0%); }
  100% { transform: translateY(100%); }
}

.about-hero {
  position: relative;
  height: 100vh;
  width: 100%;
  background-image: url('/images/lala.jpg');
  background-size: 110%;
  background-position: center;
  background-repeat: no-repeat;
  animation: zoomOut 2s ease-out 1s forwards;
}

@keyframes zoomOut {
  0% { background-size: 110%; }
  100% { background-size: 100%; }
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    to bottom,
    rgba(0, 0, 0, 0.7) 0%,
    rgba(0, 0, 0, 0.15) 20%,
    rgba(0, 0, 0, 0) 40%,
    rgba(0, 0, 0, 0) 60%,
    rgba(0, 0, 0, 0.4) 80%,
    rgba(0, 0, 0, 0.7) 100%
  );
  z-index: 1;
}

.about-text {
  position: absolute;
  bottom: 7%;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2;
  font-size: 6.25rem;
  color: white;
  font-weight: 600;
  line-height: 0.9;
  text-transform: uppercase;
  font-family: 'Rework Display Regular', sans-serif;
  letter-spacing: 0.125rem;
  margin-bottom: 0.5rem;
}

@media (max-width: 768px) {
  .about-text {
    font-size: 2rem;
  }
}

.about-quote-row {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  max-width: 1500px;
  margin: 13rem auto 30rem;
  padding: 0 2rem;
  gap: 2rem;
}

.quote-author-left {
  flex: 1;
  font-weight: 600;
  font-size: 0.9rem;
  text-transform: uppercase;
  color: #111;
  font-family: 'Rework Display Regular', sans-serif;
  text-align: left;
  margin-left: 0;
  margin-right: 4rem;
}

.quote-body {
  flex: 4;
  font-size: 2.25rem;
  line-height: 1.2;
  color: #111;
  font-family: 'Soehne', sans-serif;
  font-weight: 500;
  text-align: left;
}

@media (max-width: 768px) {
  .about-quote-row {
    flex-direction: column;
    text-align: center;
  }

  .quote-author-left {
    margin-bottom: 1rem;
  }

  .quote-body {
    font-size: 1.5rem;
  }
}
</style>
