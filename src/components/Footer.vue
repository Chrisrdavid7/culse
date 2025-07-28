<template>
  <footer class="footer">
    <div class="footer-top">
      <div class="footer-left">
        <p class="footer-logo">CUL<span>SE</span></p>
        <p class="footer-tagline">
          Fueling the cultural pulse of entertainment, fashion, and influence.
        </p>
      </div>
      <div class="footer-right">
        <div class="footer-column">
          <h4>Company</h4>
          <ul>
            <li><a href="/about">About</a></li>
            <li><a href="/ventures">Ventures</a></li>
            <li><a href="/contact">Contact</a></li>
          </ul>
        </div>
        <!-- <div class="footer-column">
          <h4>Follow</h4>
          <ul>
            <li><a href="https://instagram.com" target="_blank">Instagram</a></li>
            <li><a href="https://tiktok.com" target="_blank">TikTok</a></li>
            <li><a href="https://linkedin.com" target="_blank">LinkedIn</a></li>
          </ul>
        </div> -->
      </div>
    </div>
    <div class="footer-bottom">
      <p>© 2025 Culse Creative, LLC. All rights reserved.</p>
      <p><a href="/privacy">Privacy Policy</a> | <a href="/terms">Terms</a></p>
    </div>
  </footer>
</template>

<style scoped>
.footer {
  background-color: #111;
  color: #fff;
  padding: 3rem 1.5rem 2rem;
  font-family: 'Soehne', sans-serif;
}

.footer-top {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  align-items: flex-start;
  gap: 2rem;
  max-width: 1200px;
  margin: 0 auto 2rem;
  text-align: left;
}

.footer-left {
  flex: 1 1 300px;
}

.footer-logo {
  font-size: 1.8rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
  letter-spacing: 1px;
}

.footer-logo span {
  color: #999;
}

.footer-tagline {
  font-size: 0.95rem;
  color: #ccc;
  max-width: 400px;
  line-height: 1.5;
}

.footer-right {
  display: flex;
  flex-wrap: wrap;
  gap: 2rem;
}

.footer-column h4 {
  font-size: 1rem;
  margin-bottom: 0.5rem;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.footer-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-column li {
  margin: 0.25rem 0;
}

.footer-column a {
  color: #ccc;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-column a:hover {
  color: #fff;
}

.footer-bottom {
  text-align: center;
  font-size: 0.75rem;
  color: #777;
  border-top: 1px solid #333;
  padding-top: 1rem;
}

.footer-bottom a {
  color: #777;
  text-decoration: none;
  margin: 0 0.25rem;
}

.footer-bottom a:hover {
  color: #fff;
}

@media (max-width: 768px) {
  .footer-top {
    flex-direction: column;
    text-align: center;
    align-items: center;
  }

  .footer-right {
    justify-content: center;
  }

  .footer-column {
    min-width: 140px;
  }
}
</style>
