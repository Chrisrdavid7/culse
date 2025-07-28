<template>
  <div class="contact-page">
    <h1 class="contact-title">CONTACT</h1>
    <hr class="divider" />

    <div class="contact-grid">
      <div class="contact-item">
        <p class="label">GENERAL INQUIRIES:</p>
        <a href="mailto:info@culsecreative.com" class="link">
          info@culsecreative.com <span class="arrow">↗</span>
        </a>
      </div>
    </div>
  </div>

  <Footer />
</template>

<script setup>
import Footer from '@/components/Footer.vue'
</script>

<style scoped>
.contact-page {
  background-color: #fcfaf5;
  min-height: 100vh;
  padding: 10rem 2rem 5rem;
  font-family: 'ReworkDisplayTRIAL-Regular', sans-serif;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.contact-title {
  text-align: center;
  font-size: 5rem;
  font-weight: bold;
  text-transform: uppercase;
  margin-bottom: 2rem;
}

.divider {
  border: none;
  border-top: 1px solid #000;
  margin: 0 auto 5rem;
  width: 90%;
}

.contact-grid {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.contact-item {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.label {
  font-size: 0.85rem;
  font-weight: 600;
  text-transform: uppercase;
  margin-bottom: 0.5rem;
  color: #222;
  letter-spacing: 0.5px;
}

.link {
  font-size: 1.4rem;
  font-weight: 600;
  text-decoration: none;
  color: #000;
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
}

.link:hover {
  text-decoration: underline;
}

.arrow {
  font-size: 1rem;
}

@media (max-width: 768px) {
  .contact-title {
    font-size: 3rem;
  }

  .link {
    font-size: 1.2rem;
  }
}
</style>
