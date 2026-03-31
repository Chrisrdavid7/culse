<template>
  <Navbar />

  <!-- Slide-down overlay -->
  <div class="slide-overlay" v-if="showOverlay"></div>

  <div class="about-content">

    <!-- ── 1. HERO ── -->
    <section class="about-hero" :class="{ 'image-loaded': imageLoaded }">
      <img
        class="hero-image"
        src="/images/lala.jpg"
        alt="About Hero"
        @load="imageLoaded = true"
      />
      <div class="overlay"></div>
      <div class="hero-footer">
        <div class="hero-eyebrow">CULSE CREATIVE</div>
        <div class="about-text">ABOUT</div>
      </div>
    </section>

    <!-- ── 2. MISSION ── -->
    <section class="mission-section">
      <div class="mission-inner">
        <div class="mission-left">
          <span class="mission-label">WHO WE ARE</span>
        </div>
        <div class="mission-right">
          <p class="mission-body">
            Culse is a creative disruptor fueling culture's next wave — where iconic talent, viral moments, and boundary-breaking movements collide across entertainment, fashion, sports, and influence.
          </p>
          <div class="mission-stats">
            <div class="stat">
              <div class="stat-n">8+</div>
              <div class="stat-l">Ventures</div>
            </div>
            <div class="stat">
              <div class="stat-n">5</div>
              <div class="stat-l">Verticals</div>
            </div>
            <div class="stat">
              <div class="stat-n">100M+</div>
              <div class="stat-l">Combined reach</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ── 3. VERTICALS ── -->
    <section class="verticals-section">
      <div class="verticals-inner">
        <span class="section-label">WHAT WE DO</span>
        <div class="verticals-list">
          <div
            class="vertical-item"
            v-for="(v, i) in verticals"
            :key="i"
            :style="{ transitionDelay: i * 0.08 + 's' }"
          >
            <span class="v-num">{{ String(i + 1).padStart(2, '0') }}</span>
            <span class="v-name">{{ v }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ── 4. FEATURED WORK (carousel) ── -->
    <section class="work-section">
      <div class="work-header">
        <span class="section-label">FEATURED WORK</span>
        <h2 class="work-title">In the room<br>that matters</h2>
      </div>
      <div class="card-carousel-container">
        <div class="card-carousel-track">
          <AboutCard
            v-for="(item, index) in loopedImages"
            :key="index"
            :src="item.src"
            :alt="item.alt"
            :metric="item.metric"
            :title="item.label"
            :subtitle="item.sublabel"
            :desc="item.desc"
          />
        </div>
      </div>
    </section>

    <!-- ── 5. CTA ── -->
    <section class="about-cta">
      <div class="cta-inner">
        <p class="cta-sub">Ready to make moves?</p>
        <h2 class="cta-heading">LET'S WORK<br>TOGETHER</h2>
        <a href="/contact" class="cta-link">Get in touch ↗</a>
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

onMounted(() => {
  setTimeout(() => (showOverlay.value = false), 2500)
})

const verticals = ['Sports', 'Tech', 'Music', 'Television', 'Brands & Hospitality']

const carouselImages = [
  {
    src: '/images/badBunny.jpg',
    alt: 'Bad Bunny',
    metric: 'Brands',
    label: 'TWNTY TWO',
    sublabel: '2023',
    desc: 'Bad Bunny rocks a TWNTY-TWO snapback during his 2023 Grammys performance, bringing major attention to the emerging brand.',
  },
  {
    src: '/images/Carl.jpg',
    alt: 'Carl Radke',
    metric: 'Television',
    label: 'Carl Radke',
    sublabel: '2025',
    desc: 'Carl Radke appears on Watch What Happens Live with Andy Cohen, holding the show\'s signature question card.',
  },
  {
    src: '/images/Kiyan.jpg',
    alt: 'Kiyan Anthony',
    metric: 'Sports',
    label: 'Kiyan Anthony',
    sublabel: '2024',
    desc: 'Kiyan Anthony poses courtside at Madison Square Garden for a paid partnership with American Eagle.',
  },
  {
    src: '/images/jvke.jpg',
    alt: 'JVKE',
    metric: 'Music',
    label: 'JVKE',
    sublabel: '2023',
    desc: 'JVKE featured in Billboard Magazine.',
  },
  {
    src: '/images/Andrea.jpeg',
    alt: 'Andrea Denver',
    metric: 'Television',
    label: 'Andrea Denver',
    sublabel: '2024',
    desc: 'Andrea Denver photoshoot.',
  },
]

const loopedImages = [...carouselImages, ...carouselImages]
</script>

<style scoped>

/* ── Overlay ── */
.slide-overlay {
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100vh;
  background-color: black;
  z-index: 9999;
  animation: slideDown 2.5s ease forwards;
}
@keyframes slideDown {
  0%   { transform: translateY(0%); }
  100% { transform: translateY(100%); }
}

.about-content {
  background-color: #fcfaf5;
}

/* ── 1. Hero ── */
.about-hero {
  position: relative;
  height: 100vh;
  width: 100%;
  background-color: black;
  overflow: hidden;
}
.hero-image {
  position: absolute;
  inset: 0;
  width: 100%; height: 100%;
  object-fit: cover;
  transform: scale(1.08);
  opacity: 0;
  transition: opacity 2s ease, transform 3s ease;
}
.about-hero.image-loaded .hero-image {
  opacity: 1;
  transform: scale(1);
}
.overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to bottom,
    rgba(0,0,0,0.45) 0%,
    transparent 40%,
    rgba(0,0,0,0.65) 100%
  );
  z-index: 1;
}
.hero-footer {
  position: absolute;
  bottom: 7%;
  left: 50%;
  transform: translateX(-50%);
  z-index: 2;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
}
.hero-eyebrow {
  font-family: 'Rework Semibold', sans-serif;
  font-size: 0.7rem;
  letter-spacing: 0.35em;
  text-transform: uppercase;
  color: rgba(255,255,255,0.5);
}
.about-text {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: clamp(3.5rem, 9vw, 8rem);
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  line-height: 1;
  color: white;
}

/* ── 2. Mission ── */
.mission-section {
  padding: 10rem 4rem 8rem;
  max-width: 1500px;
  margin: 0 auto;
  border-bottom: 1px solid #e8e4dc;
}
.mission-inner {
  display: grid;
  grid-template-columns: 1fr 3fr;
  gap: 4rem;
  align-items: start;
}
.mission-label {
  font-family: 'Rework Semibold', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #999;
  padding-top: 0.5rem;
}
.mission-body {
  font-family: 'Soehne', sans-serif;
  font-size: clamp(1.6rem, 3vw, 3rem);
  font-weight: 400;
  line-height: 1.25;
  color: #111;
  margin: 0 0 4rem;
}
.mission-stats {
  display: flex;
  gap: 4rem;
  padding-top: 3rem;
  border-top: 1px solid #e8e4dc;
}
.stat-n {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: 2.5rem;
  font-weight: 600;
  color: #111;
  line-height: 1;
  margin-bottom: 0.4rem;
}
.stat-l {
  font-family: 'Rework Semibold', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #999;
}

/* ── 3. Verticals ── */
.verticals-section {
  padding: 6rem 4rem;
  max-width: 1500px;
  margin: 0 auto;
  border-bottom: 1px solid #e8e4dc;
}
.verticals-inner {
  display: grid;
  grid-template-columns: 1fr 3fr;
  gap: 4rem;
  align-items: start;
}
.section-label {
  font-family: 'Rework Semibold', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #999;
  padding-top: 0.5rem;
}
.verticals-list {
  display: flex;
  flex-direction: column;
}
.vertical-item {
  display: flex;
  align-items: baseline;
  gap: 1.5rem;
  padding: 1.4rem 0;
  border-bottom: 1px solid #e8e4dc;
  cursor: default;
  transition: padding-left 0.3s ease;
}
.vertical-item:first-child { border-top: 1px solid #e8e4dc; }
.vertical-item:hover { padding-left: 0.75rem; }
.v-num {
  font-family: 'Soehne', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.15em;
  color: #bbb;
  flex-shrink: 0;
}
.v-name {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: clamp(1.6rem, 3.5vw, 3.25rem);
  font-weight: 400;
  color: #111;
  text-transform: uppercase;
  line-height: 1;
  letter-spacing: -0.01em;
}

/* ── 4. Featured Work ── */
.work-section {
  padding: 8rem 0;
  background-color: #f5f2eb;
  border-bottom: 1px solid #e8e4dc;
  overflow: hidden;
}
.work-header {
  padding: 0 4rem 4rem;
  max-width: 1500px;
  margin: 0 auto;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
}
.work-title {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: clamp(2.5rem, 5vw, 5rem);
  font-weight: 400;
  text-transform: uppercase;
  color: #111;
  line-height: 0.95;
  letter-spacing: -0.02em;
  margin: 0;
}
.card-carousel-container {
  overflow: hidden;
  padding: 1rem 0;
}
.card-carousel-track {
  display: flex;
  gap: 1rem;
  width: max-content;
  animation: scrollLeft 50s linear infinite;
}
@keyframes scrollLeft {
  from { transform: translateX(0); }
  to   { transform: translateX(-50%); }
}

/* ── 5. CTA ── */
.about-cta {
  padding: 12rem 4rem;
  text-align: center;
  background-color: #111;
}
.cta-inner {
  max-width: 800px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1.5rem;
}
.cta-sub {
  font-family: 'Rework Semibold', sans-serif;
  font-size: 0.75rem;
  letter-spacing: 0.35em;
  text-transform: uppercase;
  color: #666;
  margin: 0;
}
.cta-heading {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: clamp(3.5rem, 9vw, 8rem);
  font-weight: 600;
  text-transform: uppercase;
  color: #f5f2eb;
  line-height: 0.9;
  letter-spacing: -0.02em;
  margin: 0;
}
.cta-link {
  margin-top: 1rem;
  font-family: 'Soehne', sans-serif;
  font-size: 1rem;
  letter-spacing: 0.1em;
  color: #f5f2eb;
  text-decoration: none;
  border-bottom: 1px solid rgba(255,255,255,0.3);
  padding-bottom: 4px;
  transition: border-color 0.3s ease, color 0.3s ease;
}
.cta-link:hover {
  color: #c4b99a;
  border-color: #c4b99a;
}

/* ── Mobile ── */
@media (max-width: 768px) {
  .mission-section  { padding: 6rem 1.5rem 5rem; }
  .mission-inner    { grid-template-columns: 1fr; gap: 2rem; }
  .mission-body     { font-size: 1.5rem; margin-bottom: 2.5rem; }
  .mission-stats    { gap: 2rem; flex-wrap: wrap; }
  .stat-n           { font-size: 2rem; }

  .verticals-section { padding: 4rem 1.5rem; }
  .verticals-inner   { grid-template-columns: 1fr; gap: 2rem; }
  .v-name            { font-size: 1.8rem; }
  .vertical-item     { padding: 1rem 0; }

  .work-section  { padding: 5rem 0; }
  .work-header   { padding: 0 1.5rem 3rem; flex-direction: column; align-items: flex-start; gap: 1rem; }
  .work-title    { font-size: 2.5rem; }

  .about-cta     { padding: 7rem 1.5rem; }
  .cta-heading   { font-size: 3.5rem; }
}
</style>
