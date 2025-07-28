<template>
    <div class="ventures-page">
      <h1 class="ventures-title">VENTURES</h1>
  
      <section class="ventures-intro">
        <p>
          At Culse, we build ventures that live at the edge of culture — where creativity meets commerce across food, fashion, music, and media.
        </p>
      </section>
  
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
            <img :src="venture.image" :alt="venture.title" class="venture-image" />
            <p class="venture-desc">{{ venture.description }}</p>
          </div>
        </a>
       </div>
       <p class="ventures-continue">To be continued...</p>


        </div>
  
    <Footer />
  </template>
  
  <script setup>
import Footer from '@/components/Footer.vue'

const ventures = [
  {
    title: "Gigz",
    image: "/images/Black_gigz.png",
    description:
      "Gigz is revolutionizing live entertainment with an AI-powered engine that connects emerging artists to elite venues worldwide — no middlemen, just momentum. Where talent meets data, opportunity follows.",
    url: "https://playgigz.com"
  },
  {
    title: "Quintyn Holdings",
    image: "/images/QWhiteBG.png",
    description:
      "Quintyn Holdings is the digital architect for the future — building high-performance websites and iconic brands for tomorrow’s most ambitious startups. Tech-forward, design-obsessed, and culture-aligned.",
    url: "https://quintynholdings.com"
  },
  {
    title: "TWNTY TWO",
    image: "/images/twntytwo.jpg",
    description:
      "TWNTY TWO is more than streetwear — it’s a cultural signal. Worn by icons, embraced by the underground, and built for those who define what’s next. Fashion that doesn’t follow trends — it creates them.",
    url: "https://twntytwo.com"
  },
  {
    title: "Famous Nobody's",
    image: "/images/famous.jpg",
    description:
      "Famous Nobody’s celebrates the unseen architects of culture. A lifestyle imprint for the bold, the brilliant, and the unbothered — blending grit with influence, and anonymity with impact.",
    url: "https://famousnobodys.com"
  },
  {
    title: "Red Lip Productions",
    image: "/images/redLip.png",
    description:
      "Red Lip Productions is a top-tier content studio redefining storytelling across film, television, and digital. From concept to global screen, we create unforgettable visuals that spark culture and conversation.",
    url: "https://redlipproductions.com"
  },
  {
    title: "9 Jones",
    image: "/images/9jones.jpg",
    description:
      "9 Jones is nightlife reimagined — a members-only experience where luxury, sound, and style collide. More than a venue, it’s a vibe engineered for the influential and unforgettable.",
    url: "https://9jones.com"
  },
]
</script>

  
  <style scoped>
  .ventures-page {
    background-color: #fcfaf5;
    padding: 10rem 2rem 6rem;
    min-height: 100vh;
    text-align: center;
  }
  
  .ventures-title {
    font-size: clamp(2.5rem, 6vw, 6rem);
    font-weight: 600;
    text-transform: uppercase;
    font-family: 'Rework Display Regular', sans-serif;
    margin-bottom: 4rem;
    letter-spacing: 0.1rem;
  }
  
  .ventures-intro p {
    font-size: 1.25rem;
    max-width: 800px;
    margin: 0 auto 6rem;
    color: #333;
    font-family: 'Soehne', sans-serif;
    line-height: 1.5;
  }
  
  .ventures-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 4rem;
    max-width: 1200px;
    margin: 0 auto;
  }
  
  .venture-link {
    text-decoration: none;
    color: inherit;
  }
  
  /* Base venture card */
  .venture-card {
    background-color: #fff;
    padding: 2rem;
    border-radius: 1.5rem;
    box-shadow: 0 6px 20px rgba(0, 0, 0, 0.06);
    text-align: left;
    transition: transform 0.3s ease;
  }
  
  /* Slanted layout (desktop only) */
  .venture-link:nth-child(1) .venture-card { margin-top: 0rem; }
  .venture-link:nth-child(2) .venture-card { margin-top: 5rem; }
  .venture-link:nth-child(3) .venture-card { margin-top: 10rem; }
  .venture-link:nth-child(4) .venture-card { margin-top: -10rem; }
  .venture-link:nth-child(5) .venture-card { margin-top: -3rem; }
  .venture-link:nth-child(6) .venture-card { margin-top: 5rem; }
  
  .venture-card:hover {
    transform: translateY(-6px);
  }
  
  .venture-image {
    width: 100%;
    height: auto;
    border-radius: 1rem;
    margin-bottom: 1.25rem;
  }
  
  .venture-desc {
    font-size: 1rem;
    color: #555;
    font-family: 'Soehne', sans-serif;
    line-height: 1.4;
  }
  
  /* Tablet */
  @media (max-width: 1024px) {
    .ventures-grid {
      grid-template-columns: repeat(2, 1fr);
    }
  }
  
  /* Mobile */
  @media (max-width: 640px) {
    .ventures-grid {
      grid-template-columns: 1fr;
    }
  
    .ventures-page {
      padding-top: 6rem;
    }
  
    /* Remove staggered margins on mobile */
    .venture-card {
      margin-top: 0 !important;
    }
  
    .venture-desc {
      font-size: 0.95rem;
    }
  }
  .ventures-continue {
  text-align: center;
  font-size: 1.1rem;
  font-style: italic;
  color: #888;
  margin-top: 4rem;
  font-family: 'Soehne', sans-serif;
}

  </style>
  