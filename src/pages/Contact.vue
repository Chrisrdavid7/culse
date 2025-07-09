<template>
  <div class="contact-page">
    <h1 class="contact-title">CONTACT</h1>
    <hr class="divider" />

    <div class="contact-grid">
      <div class="contact-item">
        <p class="label">GENERAL INQUIRIES:</p>
        <a href="mailto:inquiries@culsecreative.com" class="link">
          inquiries@culsecreative.com <span class="arrow">↗</span>
        </a>
      </div>

      <div class="contact-item">
        <p class="label">LINKEDIN:</p>
        <a href="https://linkedin.com/company/culse" target="_blank" class="link">
          culse-creative <span class="arrow">↗</span>
        </a>
      </div>

      <div class="contact-item">
        <p class="label">PRESS:</p>
        <a href="mailto:press@culsecreative.com" class="link">
          press@culsecreative.com <span class="arrow">↗</span>
        </a>
      </div>

      <div class="contact-item">
        <p class="label">CAREER OPPORTUNITIES:</p>
        <a href="https://culsecreative.com/careers" target="_blank" class="link">
          CULSE career opportunities <span class="arrow">↗</span>
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.contact-page {
  background-color: #fcfaf5;
  min-height: 100vh;
  padding: 10rem 2rem 5rem;
  font-family: 'ReworkDisplayTRIAL-Regular', sans-serif;
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
  max-width: 1100px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem 6rem;
}

.contact-item {
  display: flex;
  flex-direction: column;
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
  .contact-grid {
    grid-template-columns: 1fr;
  }
  .contact-title {
    font-size: 3rem;
  }
}
</style>
