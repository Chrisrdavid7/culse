<template>
  <div class="expertise-home-section">
    <div class="grid">
      <div
        class="expertise-section"
        v-for="(section, index) in sections"
        :key="index"
      >
        <h2 class="section-title">{{ section.title }}</h2>
        <div class="image-wrapper">
          <img
            :src="section.image"
            :alt="section.title"
            class="section-image"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  sections: {
    type: Array,
    required: true,
  },
});
</script>

<style scoped>
.expertise-home-section {
  margin-top: 6rem;
  padding: 2rem;
  background-color: #fcfaf5;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 items per row on desktop */
  gap: 2rem;
  max-width: 1500px;
  margin: 0 auto;
  padding: 0 2rem;
}

/* Tablet */
@media (max-width: 1024px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Mobile */
@media (max-width: 640px) {
  .grid {
    grid-template-columns: 1fr;
    gap: 3rem;
  }

  .expertise-section {
    margin: 0;
    padding: 0 1rem;
  }

  .section-title {
    font-size: 1rem;
    margin-bottom: 0.5rem;
    text-align: left;
  }

  .section-image {
    border-radius: 2px;
  }

  /* Remove nth-child margins on mobile */
  .expertise-section:nth-child(n) {
    margin-top: 0 !important;
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
  display: block;
}

.section-image:hover {
  transform: scale(1.05);
}

/* Staggered layout (only for desktop) */
@media (min-width: 1025px) {
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
}
</style>
