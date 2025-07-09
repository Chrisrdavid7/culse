<template>
  <div class="expertise-page">
    <h1  id="scroll-section" class="title">EXPERTISE</h1>
    <div class="grid">
      <div  class="expertise-section" v-for="(section, index) in sections" :key="index">
        <h2 class="section-title">{{ section.title }}</h2>
        <div class="image-wrapper">
  <img :src="section.image" :alt="section.title" class="section-image" />
</div>

      </div>
    </div>
  </div>
  <Footer />
</template>

<script setup>



import { onMounted } from 'vue'
import Footer from '@/components/Footer.vue'

onMounted(() => {
  const savedScrollY = parseInt(localStorage.getItem('scrollY')) || 0
  const offset = 150 // adjust this as needed
  window.scrollTo({
    top: savedScrollY + offset,
    behavior: 'smooth'
  })
})


const sections = [
  {
    title: "SPORTS",
    image: "/images/Melo.jpg", // Replace with your actual image
  },
  {
    title: "FASHION",
    image: "/images/Ciara.jpg",
  },
  {
    title: "BRANDS",
    image: "/images/Kiyan.jpg",
  },
  {
    title: "Music",
    image: "/images/jvke.jpg",
  },
  {
    title: "Television",
    image: "/images/Andrea.jpeg", // Replace with your actual image
  },
 
  {
    title: "Hospitality",
    image: "/images/Cindy.jpg",
  },
  {
    title: "Culture and Influence",
    image: "/images/kai.jpg",
  },
  // Add more as needed
]
</script>

<style scoped>
.expertise-page {
  background-color: #fcfaf5;
  padding: 13rem 2rem 3rem;
  min-height: 100vh;
}

.title {
  font-size: clamp(2.5rem, 6vw, 6.25rem); /* fluid size */
  letter-spacing: 0.25rem;
  line-height: 1;
  font-weight: 600;
  text-align: center;
  margin-bottom: 12rem;
  text-transform: uppercase;
  font-family: 'Rework Display Regular', sans-serif;
  word-break: break-word;
  padding: 0 1rem;
  text-shadow: 1px 1px 2px rgba(0,0,0,0.08);
  animation: fadeIn 1s ease-out;
}

/* Tablet */
@media (max-width: 1024px) {
  .title {
    font-size: 4rem;
    letter-spacing: 0.2rem;
    margin-bottom: 6rem;
  }
}

/* Mobile */
@media (max-width: 640px) {
  .title {
    font-size: 2.5rem;
    letter-spacing: 0.1rem;
    margin-bottom: 4rem;
    padding: 0 1rem;
  }
}
.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* keep 3 per row */
  gap: 2rem; /* reduce gap between images */
  max-width: 1500px;
  margin: 0 auto;
}

@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 640px) {
  .grid {
    grid-template-columns: 1fr;
  }
}


.expertise-section {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin: 0;
}

.expertise-section:nth-child(1) {
  margin-top: 0rem;
}

.expertise-section:nth-child(2) {
  margin-top: 9rem;
}

.expertise-section:nth-child(3) {
  margin-top: 21rem;
}
.expertise-section:nth-child(4) {
  margin-top: -13em;
}

.expertise-section:nth-child(5) {
  margin-top: -4rem;
}

.expertise-section:nth-child(6) {
  margin-top: 3rem;
}
.expertise-section:nth-child(7) {
  margin-top: -20rem;
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
  margin: 0; /* remove extra space around image */
}

.section-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  transition: transform 0.9s ease;
  display: block; /* eliminate inline spacing */
}

.section-image:hover {
  transform: scale(1.05); /* Only the image zooms */
}
@media (max-width: 640px) {
  .expertise-section {
    margin-top: 0 !important;
  }

  .expertise-section:nth-child(1),
  .expertise-section:nth-child(2),
  .expertise-section:nth-child(3),
  .expertise-section:nth-child(4),
  .expertise-section:nth-child(5),
  .expertise-section:nth-child(6),
  .expertise-section:nth-child(7) {
    margin-top: 3rem; /* or adjust as needed */
  }

  .grid {
    gap: 3rem;
  }

  .section-image {
    height: auto;
  }
}


</style>
