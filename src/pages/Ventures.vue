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
          <div class="card-image-wrap">
            <img :src="venture.image" :alt="venture.title" class="venture-image" />
            <div class="image-overlay"></div>
          </div>
          <div class="card-body">
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
    image: "/images/GigzLogo.png",
    description:
      "Gigz is revolutionizing live entertainment with an AI-powered engine that connects emerging artists to elite venues worldwide — no middlemen, just momentum. Where talent meets data, opportunity follows.",
    url: "https://playgigz.com"
  },
  {
    title: "TWNTY TWO",
    image: "/images/twntytwo.jpg",
    description:
      "TWNTY TWO is more than streetwear — it's a cultural signal. Worn by icons, embraced by the underground, and built for those who define what's next. Fashion that doesn't follow trends — it creates them.",
    url: "https://twnty-two.com/"
  },
  {
    title: "Quintyn Holdings",
    image: "/images/QWhiteBG.png",
    description:
      "Quintyn Holdings is the digital architect for the future — building high-performance websites and iconic brands for tomorrow's most ambitious startups. Tech-forward, design-obsessed, and culture-aligned.",
    url: "https://quintynholdings.com"
  },
  {
    title: "Famous Nobody's",
    image: "/images/famous.jpg",
    description:
      "Famous Nobody's celebrates the unseen architects of culture. A lifestyle imprint for the bold, the brilliant, and the unbothered — blending grit with influence, and anonymity with impact.",
    url: "https://famousnobodys.com"
  },
  {
    title: "Red Lip Productions",
    image: "/images/redLip.png",
    description:
      "Red Lip Productions is a top-tier content studio redefining storytelling across film, television, and digital. From concept to global screen, we create unforgettable visuals that spark culture and conversation.",
    url: "https://chelseycreative.com"
  },
  {
    title: "9 Jones",
    image: "/images/9jones.jpg",
    description:
      "9 Jones is nightlife reimagined — a members-only experience where luxury, sound, and style collide. More than a venue, it's a vibe engineered for the influential and unforgettable.",
    url: "https://www.instagram.com/9jonesnyc/?hl=en"
  },
  {
    title: "Festication",
    image: "/images/festication.png",
    description:
      "Festication is redefining the destination festival — pairing world-class artist lineups with all-inclusive luxury resorts across Mexico and the Caribbean. Intimate performances, curated fan experiences, and a new standard for how music and travel collide.",
    url: "https://festication.com"
  },
  {
    title: "Ember Shores",
    image: "/images/embers.png",
    description:
      "Ember Shores is the flagship destination festival experience — an intimate, all-inclusive escape on the shores of Mexico featuring handpicked headliners, premium production, and moments that outlast the weekend. Where the music never stops and the sun never sets on the good time.",
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

.dot {
  color: #4a4840;
}

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

/* Staggered vertical offset — col 2 drops, col 3 drops more */
.venture-link:nth-child(3n+2) .venture-card { margin-top: 6rem; }
.venture-link:nth-child(3n+3) .venture-card { margin-top: 12rem; }

/* Entrance animation */
.venture-link {
  text-decoration: none;
  color: inherit;
  opacity: 0;
  animation: fadeUp 0.7s cubic-bezier(0.22, 1, 0.36, 1) forwards;
}

.venture-link:nth-child(1) { animation-delay: 0.05s; }
.venture-link:nth-child(2) { animation-delay: 0.15s; }
.venture-link:nth-child(3) { animation-delay: 0.25s; }
.venture-link:nth-child(4) { animation-delay: 0.35s; }
.venture-link:nth-child(5) { animation-delay: 0.45s; }
.venture-link:nth-child(6) { animation-delay: 0.55s; }

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
  box-shadow: 0 24px 64px rgba(0, 0, 0, 0.5);
}

/* ─── Card Top Row (index + arrow) ──────────────────────────── */

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
  font-weight: 400;
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

/* ─── Image ──────────────────────────────────────────────────── */

.card-image-wrap {
  position: relative;
  overflow: hidden;
  aspect-ratio: 4 / 3;
}

.venture-image {
  width: 100%;
  height: 100%;
  object-fit: contain;
  object-position: center;
  display: block;
  padding: 1.75rem;
  box-sizing: border-box;
  transition: transform 0.6s cubic-bezier(0.22, 1, 0.36, 1);
  filter: brightness(0.92) saturate(0.9);
}

.venture-card:hover .venture-image {
  transform: scale(1.04);
  filter: brightness(1) saturate(1);
}

.venture-card:hover .venture-image {
  transform: scale(1.06);
  filter: brightness(1) saturate(1);
}

.image-overlay {
  display: none;
}

/* ─── Card Body ─────────────────────────────────────────────── */

.card-body {
  padding: 1.5rem 1.5rem 2rem;
}

.venture-name {
  font-family: 'Rework Display Regular', sans-serif;
  font-size: 1.6rem;
  font-weight: 400;
  letter-spacing: 0.01em;
  color: #e8e2d9;
  margin: 0 0 0.75rem;
  line-height: 1.1;
}

.venture-desc {
  font-family: 'Soehne', sans-serif;
  font-size: 0.85rem;
  line-height: 1.6;
  color: #6a6560;
  margin: 0;
  transition: color 0.3s ease;
}

.venture-card:hover .venture-desc {
  color: #8a8278;
}

/* ─── Footer Coda ────────────────────────────────────────────── */

.ventures-end {
  display: flex;
  align-items: center;
  gap: 2rem;
  max-width: 1280px;
  margin: 8rem auto 0;
  padding: 0 4rem;
}

.end-line {
  flex: 1;
  height: 1px;
  background-color: #2a2924;
}

.ventures-continue {
  font-family: 'Soehne', sans-serif;
  font-size: 0.72rem;
  letter-spacing: 0.22em;
  text-transform: uppercase;
  color: #4a4840;
  white-space: nowrap;
  margin: 0;
  font-style: normal;
}

/* ─── Tablet ──────────────────────────────────────────────────── */

@media (max-width: 1024px) {
  .ventures-grid {
    grid-template-columns: repeat(2, 1fr);
    padding: 0 2rem;
  }

  .ventures-header {
    padding: 8rem 2rem 0;
  }

  /* Reset 3-column stagger, apply 2-column stagger */
  .venture-link:nth-child(3n+2) .venture-card { margin-top: 0; }
  .venture-link:nth-child(3n+3) .venture-card { margin-top: 0; }
  .venture-link:nth-child(2n)   .venture-card { margin-top: 5rem; }

  .ventures-end {
    padding: 0 2rem;
  }
}

/* ─── Mobile ──────────────────────────────────────────────────── */

@media (max-width: 640px) {
  .ventures-grid {
    grid-template-columns: 1fr;
    padding: 0 1.25rem;
    gap: 1rem;
  }

  .ventures-header {
    padding: 6rem 1.25rem 0;
  }

  .ventures-title {
    font-size: clamp(3rem, 14vw, 5rem);
  }

  /* Kill all stagger on mobile */
  .venture-link:nth-child(n) .venture-card {
    margin-top: 0 !important;
  }

  .ventures-end {
    margin-top: 5rem;
    padding: 0 1.25rem;
  }
}
</style>
