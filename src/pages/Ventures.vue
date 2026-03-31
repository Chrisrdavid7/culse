<template>
  <div class="ventures-page">

    <header class="ventures-header">
      <div class="header-eyebrow">
        <span>CULSE CREATIVE</span>
        <span class="dot">·</span>
        <span>PORTFOLIO</span>
      </div>
      <h1 class="ventures-title">VENTURES</h1>
      <div class="header-rule"></div>
      <section class="ventures-intro">
        <p>
          At Culse, we build ventures that live at the edge of culture —
          where creativity meets commerce across food, fashion, music, and media.
        </p>
      </section>
    </header>

    <div class="ventures-grid">
      <a
        v-for="(venture, index) in ventures"
        :key="index"
        :href="venture.url"
        target="_blank"
        rel="noopener"
        class="venture-link"
      >
        <div class="venture-card">
          <div class="card-top">
            <span class="card-index">{{ String(index + 1).padStart(2, '0') }}</span>
            <span class="card-arrow">↗</span>
          </div>

          <div
            class="card-image-wrap"
            :class="venture.imageType === 'logo' ? 'logo-card' : 'photo-card'"
            :style="venture.imageType === 'logo' ? { background: venture.logoBg || '#161612' } : {}"
          >
            <img
              :src="venture.image"
              :alt="venture.title"
              class="venture-image"
              :class="venture.imageType === 'logo' ? 'img-logo' : 'img-photo'"
            />
            <div class="image-overlay"></div>
          </div>

          <div class="card-body">
            <span class="venture-category">{{ venture.category }}</span>
            <h2 class="venture-name">{{ venture.title }}</h2>
            <p class="venture-desc">{{ venture.description }}</p>
          </div>
        </div>
      </a>
    </div>

    <div class="ventures-end">
      <div class="end-line"></div>
      <p class="ventures-continue">To be continued</p>
      <div class="end-line"></div>
    </div>

    <Footer />
  </div>
</template>

<script setup>
import Footer from '@/components/Footer.vue'

const ventures = [
  {
    title: "Gigz",
    category: "Technology · Live Entertainment",
    image: "/images/GigzLogo.png",
    imageType: "logo",          // swap to "photo" once you have a real image
    logoBg: "#0d0d0d",
    description: "Revolutionizing live entertainment with an AI-powered engine that connects emerging artists to elite venues worldwide — no middlemen, just momentum.",
    url: "https://playgigz.com"
  },
  {
    title: "TWNTY TWO",
    category: "Fashion · Streetwear",
    image: "/images/twntytwo.jpg",
    imageType: "photo",
    description: "More than streetwear — a cultural signal. Worn by icons, embraced by the underground, built for those who define what's next.",
    url: "https://twnty-two.com/"
  },
  {
    title: "Quintyn Holdings",
    category: "Technology · Branding",
    image: "/images/QWhiteBG.png",
    imageType: "logo",
    logoBg: "#f5f2eb",          // white bg to match the logo's own background
    description: "The digital architect for the future — building high-performance websites and iconic brands for tomorrow's most ambitious startups.",
    url: "https://quintynholdings.com"
  },
  {
    title: "Famous Nobody's",
    category: "Lifestyle · Culture",
    image: "/images/famous.jpg",
    imageType: "photo",
    description: "A lifestyle imprint for the bold, the brilliant, and the unbothered — blending grit with influence, and anonymity with impact.",
    url: "https://famousnobodys.com"
  },
  {
    title: "Red Lip Productions",
    category: "Film · Television",
    image: "/images/redLip.png",
    imageType: "logo",
    logoBg: "#100a0b",
    description: "A content studio redefining storytelling across film, television, and digital. From concept to global screen, we create visuals that spark culture.",
    url: "https://chelseycreative.com"
  },
  {
    title: "9 Jones",
    category: "Nightlife · Luxury",
    image: "/images/9jones.jpg",
    imageType: "photo",
    description: "Nightlife reimagined — a members-only experience where luxury, sound, and style collide. More than a venue, it's a vibe engineered for the unforgettable.",
    url: "https://www.instagram.com/9jonesnyc/?hl=en"
  },
  {
    title: "Festication",
    category: "Festivals · Travel",
    image: "/images/festication.png",
    imageType: "logo",
    logoBg: "#0a1010",
    description: "Redefining the destination festival — world-class lineups paired with all-inclusive luxury resorts across Mexico and the Caribbean.",
    url: "https://festication.com"
  },
  {
    title: "Ember Shores",
    category: "Music Festival · Mexico",
    image: "/images/embers.png",
    imageType: "logo",
    logoBg: "#120805",
    description: "An intimate, all-inclusive escape on the shores of Mexico featuring handpicked headliners, premium production, and moments that outlast the weekend.",
    url: "https://embershores.com/"
  },
]
</script>

<style scoped>

/* ─── Page Shell ─────────────────────────────────────────────── */
.ventures-page {
  background-color: #0e0e0b;
  min-height: 100vh;
  padding: 0 0 6rem;
  color: #e8e2d9;
}

/* ─── Header ─────────────────────────────────────────────────── */
.ventures-header {
  padding: 10rem 4rem 0;
  max-width: 1280px;
  margin: 0 auto;
}
.header-eyebrow {
  font-family: 'Soehne', sans-serif;
  font-size: 0.7rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: #7a7568;
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
}
.dot { color: #4a4840; }
.ventures-title {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: clamp(4rem, 10vw, 9rem);
  font-weight: 400;
  text-transform: uppercase;
  letter-spacing: -0.02em;
  color: #f0ebe2;
  line-height: 0.95;
  margin: 0 0 3rem;
}
.header-rule {
  width: 100%;
  height: 1px;
  background: linear-gradient(to right, #3a3830, transparent);
  margin-bottom: 3rem;
}
.ventures-intro {
  max-width: 580px;
  margin-bottom: 7rem;
}
.ventures-intro p {
  font-family: 'Soehne', sans-serif;
  font-size: 1.1rem;
  line-height: 1.7;
  color: #7a7568;
  margin: 0;
}

/* ─── Grid ───────────────────────────────────────────────────── */
.ventures-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 4rem;
  align-items: start;
}
.venture-link:nth-child(3n+2) .venture-card { margin-top: 6rem; }
.venture-link:nth-child(3n+3) .venture-card { margin-top: 12rem; }

.venture-link {
  text-decoration: none;
  color: inherit;
  opacity: 0;
  animation: fadeUp 0.7s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}
.venture-link:nth-child(1) { animation-delay: 0.05s; }
.venture-link:nth-child(2) { animation-delay: 0.12s; }
.venture-link:nth-child(3) { animation-delay: 0.19s; }
.venture-link:nth-child(4) { animation-delay: 0.26s; }
.venture-link:nth-child(5) { animation-delay: 0.33s; }
.venture-link:nth-child(6) { animation-delay: 0.40s; }
.venture-link:nth-child(7) { animation-delay: 0.47s; }
.venture-link:nth-child(8) { animation-delay: 0.54s; }

@keyframes fadeUp {
  from { opacity: 0; transform: translateY(28px); }
  to   { opacity: 1; transform: translateY(0); }
}

/* ─── Card ───────────────────────────────────────────────────── */
.venture-card {
  background-color: #161612;
  border: 1px solid #2a2924;
  overflow: hidden;
  transition: border-color 0.4s ease, box-shadow 0.4s ease;
  cursor: pointer;
}
.venture-card:hover {
  border-color: #4a4638;
  box-shadow: 0 24px 64px rgba(0, 0, 0, 0.6);
}

/* ─── Card Top ───────────────────────────────────────────────── */
.card-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 1.25rem;
  border-bottom: 1px solid #1e1e1a;
}
.card-index {
  font-family: 'Soehne', sans-serif;
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  color: #4a4840;
}
.card-arrow {
  font-size: 0.9rem;
  color: #4a4840;
  transition: color 0.3s ease, transform 0.3s ease;
  display: inline-block;
}
.venture-card:hover .card-arrow {
  color: #c4b99a;
  transform: translate(2px, -2px);
}

/* ─── Image wrapper ──────────────────────────────────────────── */
.card-image-wrap {
  position: relative;
  overflow: hidden;
  aspect-ratio: 3 / 2;
}

/* PHOTO cards — cover fills the frame */
.photo-card .venture-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  display: block;
  transition: transform 0.7s cubic-bezier(0.22, 1, 0.36, 1);
  filter: brightness(0.88) saturate(0.85);
}
.photo-card:hover .venture-image {
  transform: scale(1.06);
  filter: brightness(1) saturate(1);
}

/* LOGO cards — contain keeps the logo whole, centered */
.logo-card {
  display: flex;
  align-items: center;
  justify-content: center;
}
.logo-card .venture-image {
  width: 60%;
  height: 70%;
  object-fit: contain;
  object-position: center;
  display: block;
  transition: transform 0.5s cubic-bezier(0.22, 1, 0.36, 1), opacity 0.3s ease;
  opacity: 0.9;
}
.venture-card:hover .logo-card .venture-image {
  transform: scale(1.06);
  opacity: 1;
}

/* Gradient overlay — only meaningful on photo cards */
.image-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(to bottom, transparent 40%, rgba(14,14,11,0.55) 100%);
  opacity: 0;
  transition: opacity 0.4s ease;
  pointer-events: none;
}
.photo-card:hover .image-overlay { opacity: 1; }

/* ─── Card Body ─────────────────────────────────────────────── */
.card-body {
  padding: 1.25rem 1.5rem 1.75rem;
}
.venture-category {
  display: block;
  font-family: 'Soehne', sans-serif;
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #4a4840;
  margin-bottom: 0.5rem;
}
.venture-name {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: 1.6rem;
  font-weight: 400;
  letter-spacing: 0.01em;
  color: #e8e2d9;
  margin: 0 0 0.65rem;
  line-height: 1.1;
}
.venture-desc {
  font-family: 'Soehne', sans-serif;
  font-size: 0.85rem;
  line-height: 1.65;
  color: #5a5650;
  margin: 0;
  transition: color 0.3s ease;
}
.venture-card:hover .venture-desc { color: #7a7568; }

/* ─── Footer Coda ────────────────────────────────────────────── */
.ventures-end {
  display: flex;
  align-items: center;
  gap: 2rem;
  max-width: 1280px;
  margin: 8rem auto 0;
  padding: 0 4rem;
}
.end-line { flex: 1; height: 1px; background-color: #2a2924; }
.ventures-continue {
  font-family: 'Soehne', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: #4a4840;
  white-space: nowrap;
  margin: 0;
}

/* ─── Tablet ─────────────────────────────────────────────────── */
@media (max-width: 1024px) {
  .ventures-grid { grid-template-columns: repeat(2, 1fr); padding: 0 2rem; }
  .ventures-header { padding: 8rem 2rem 0; }
  .venture-link:nth-child(3n+2) .venture-card { margin-top: 0; }
  .venture-link:nth-child(3n+3) .venture-card { margin-top: 0; }
  .venture-link:nth-child(2n)   .venture-card { margin-top: 5rem; }
  .ventures-end { padding: 0 2rem; }
}

/* ─── Mobile ─────────────────────────────────────────────────── */
@media (max-width: 640px) {
  .ventures-grid { grid-template-columns: 1fr; padding: 0 1.25rem; gap: 1rem; }
  .ventures-header { padding: 6rem 1.25rem 0; }
  .ventures-title { font-size: clamp(3rem, 14vw, 5rem); }
  .venture-link:nth-child(n) .venture-card { margin-top: 0 !important; }
  .ventures-end { margin-top: 5rem; padding: 0 1.25rem; }
}
</style>
