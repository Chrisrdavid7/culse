<template>
  <Navbar />

  <div class="about-content">
    <!-- Overlay -->
    <div class="slide-overlay" v-if="showOverlay"></div>

    <!-- Hero -->
    <section class="about-hero" :class="{ 'image-loaded': imageLoaded }">
      <img
        class="hero-image"
        src="/images/lala.jpg"
        alt="About Hero"
        @load="imageLoaded = true"
      />
      <div class="overlay"></div>
      <div class="about-text">ABOUT</div>
    </section>

    <!-- Quote -->
    <section class="about-quote-row">
      <div class="quote-author-left">CULSE</div>
      <div class="quote-body">
        <p>
          Culse is a creative disruptor fueling culture’s next wave — where iconic talent, viral moments, and boundary-breaking movements collide across entertainment, fashion, sports, and influence.
        </p>
      </div>
    </section>

    <!-- ✨ Endless Auto-Scroll Carousel -->
    <section class="card-carousel-container">
      <div class="card-carousel-track">
        <AboutCard
          v-for="(image, index) in loopedImages"
          :key="index"
          :src="image.src"
          :alt="image.alt"
          :metric="image.metric"
          :title="image.label"
          :subtitle="image.sublabel"
          :desc="image.desc"
        />
      </div>
    </section>

    <!-- Expertise Section (formerly Expertise.vue) -->
<section class="expertise-page">
  <h1 id="scroll-section" class="title">EXPERTISE</h1>
  <div class="grid">
    <div class="expertise-section" v-for="(section, index) in sections" :key="index">
      <h2 class="section-title">{{ section.title }}</h2>
      <div class="image-wrapper">
        <img :src="section.image" :alt="section.title" class="section-image" />
      </div>
    </div>
  </div>
</section>

  </div>

  <Footer />
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Navbar from '../components/Navbar.vue'
import Footer from '@/components/Footer.vue'
import AboutCard from '@/components/AboutCard.vue'

const showOverlay = ref(true)
const imageLoaded = ref(false)

const carouselImages = [
  {
    src: '/images/badBunny.jpg',
    alt: 'Bunny',
    metric: 'Brands',
    label: 'TWNTY TWO',
    sublabel: '2023',
    desc: 'Bad Bunny rocks a TWNTY-TWO snapback during his 2023 Grammys performance, bringing major attention to the emerging brand.',
  },
  {
    src: '/images/Carl.jpg',
    alt: 'Carl',
    metric: 'Television',
    label: 'Carl Radke',
    sublabel: '2025',
    desc: 'Carl Radke appears on Watch What Happens Live with Andy Cohen, flashing a confident smile while holding the show’s signature question card.',
  },
  {
    src: '/images/Kiyan.jpg',
    alt: 'Kiyan',
    metric: 'Sports',
    label: 'Kiyan Anthony',
    sublabel: '2024',
    desc: 'Kiyan Anthony poses courtside at Madison Square Garden for a paid partnership with American Eagle, blending street style with effortless cool.',
  },
  {
    src: '/images/jvke.jpg',
    alt: 'JVKE',
    metric: 'Music',
    label: 'JVKE',
    sublabel: '2023',
    desc: 'Jvke poses for Billboard Magizine.',
  },
  {
    src: '/images/Andrea.jpeg',
    alt: 'Andrea',
    metric: 'Television',
    label: 'Andrea Denver',
    sublabel: '2024',
    desc: 'Andrea Denver Photoshoot',
  },
]

// Duplicate the images to create an endless loop
const loopedImages = [...carouselImages, ...carouselImages]

onMounted(() => {
  setTimeout(() => (showOverlay.value = false), 2500)
})

const sections = [
  { title: "SPORTS", image: "/images/Melo.jpg" },
  { title: "FASHION", image: "/images/Ciara.jpg" },
  { title: "BRANDS", image: "/images/Kiyan.jpg" },
  { title: "Music", image: "/images/jvke.jpg" },
  { title: "Television", image: "/images/Andrea.jpeg" },
  { title: "Hospitality", image: "/images/Cindy.jpg" },
 
]

</script>

<style scoped>
.about-content {
  position: relative;
  z-index: 1;
  padding-bottom: 8rem;
}

/* Slide Overlay Animation */
.slide-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  background-color: black;
  z-index: 9999;
  animation: slideDown 2.5s ease forwards;
}

@keyframes slideDown {
  0% { transform: translateY(0%); }
  100% { transform: translateY(100%); }
}

/* Hero Section */
.about-hero {
  position: relative;
  height: 100vh;
  width: 100%;
  background-color: black;
  overflow: hidden;
}

.hero-image {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  object-fit: cover;
  transform: scale(1.1);
  opacity: 0;
  transition: opacity 2s ease, transform 3s ease;
  z-index: 0;
}

.about-hero.image-loaded .hero-image {
  opacity: 1;
  transform: scale(1);
}

.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, rgba(0, 0, 0, 0.7), transparent 60%, rgba(0, 0, 0, 0.7));
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
  text-transform: uppercase;
  font-family: 'Rework Display Regular', sans-serif;
  letter-spacing: 0.125rem;
  line-height: 0.9;
}

@media (max-width: 768px) {
  .about-text {
    font-size: 2rem;
  }
}

/* Quote Section */
.about-quote-row {
  display: flex;
  justify-content: space-between;
  height: 50vh;
  max-width: 1500px;
  margin: 13rem auto 6rem;
  padding: 0 2rem;
  gap: 2rem;
}

.quote-author-left {
  flex: 1;
  font-size: 0.9rem;
  font-weight: 600;
  text-transform: uppercase;
  color: #111;
  font-family: 'Rework Display Regular', sans-serif;
}

.quote-body {
  flex: 4;
  font-size: 3.25rem;
  font-family: 'Soehne', sans-serif;
  font-weight: 500;
  color: #111;
  line-height: 1.2;
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

/* Auto-Scroll Carousel */
.card-carousel-container {
  overflow: hidden;
  padding: 4rem 0;
  background-color: #fcfaf5;
}

.card-carousel-track {
  display: flex;
  gap: 1rem;
  width: max-content;
  animation: scrollLeft 60s linear infinite;
}

@keyframes scrollLeft {
  from {
    transform: translateX(0%);
  }
  to {
    transform: translateX(-50%);
  }
}

/* Tagline */
.about-bottom-tagline {
  font-size: 6.25rem;
  text-align: center;
  text-transform: uppercase;
  font-family: 'Rework Display Regular', sans-serif;
  font-weight: 600;
  color: #111;
  line-height: 0.9;
  letter-spacing: 0.125rem;
  margin: 8rem 0 4rem;
}

@media (max-width: 768px) {
  .about-bottom-tagline {
    font-size: 2.5rem;
  }
}
.expertise-page {
  background-color: #fcfaf5;
  padding: 13rem 2rem 3rem;
  min-height: 100vh;
}

.title {
  font-size: clamp(2.5rem, 6vw, 6.25rem);
  letter-spacing: 0.25rem;
  line-height: 1;
  font-weight: 600;
  text-align: center;
  margin-bottom: 12rem;
  text-transform: uppercase;
  font-family: 'Rework Display Regular', sans-serif;
  padding: 0 1rem;
  text-shadow: 1px 1px 2px rgba(0,0,0,0.08);
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 2rem;
  max-width: 1500px;
  margin: 0 auto;
}

@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
  .title {
    font-size: 4rem;
    letter-spacing: 0.2rem;
    margin-bottom: 6rem;
  }
}

@media (max-width: 640px) {
  .grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }
  .title {
    font-size: 2.5rem;
    margin-bottom: 4rem;
    letter-spacing: 0.1rem;
  }
}

.expertise-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.expertise-section:nth-child(1) { margin-top: 0rem; }
.expertise-section:nth-child(2) { margin-top: 9rem; }
.expertise-section:nth-child(3) { margin-top: 21rem; }
.expertise-section:nth-child(4) { margin-top: -13em; }
.expertise-section:nth-child(5) { margin-top: -4rem; }
.expertise-section:nth-child(6) { margin-top: 3rem; }
.expertise-section:nth-child(7) { margin-top: -20rem; }

@media (max-width: 640px) {
  .expertise-section {
    margin-top: 3rem !important;
  }
}

.section-title {
  font-size: 1rem;
  font-weight: 600;
  margin-bottom: 1rem;
  text-transform: uppercase;
  font-family: 'Rework Semibold', sans-serif;
}

.image-wrapper {
  width: 100%;
  overflow: hidden;
  border-radius: 2px;
}

.section-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  transition: transform 0.9s ease;
}

.section-image:hover {
  transform: scale(1.05);
}

</style>
