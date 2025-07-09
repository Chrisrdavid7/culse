<template>
  <nav :class="['navbar', (isBlackPage || isScrolled) ? 'navbar-black' : '']">
    <router-link to="/" class="logo" exact-active-class="active">CULSE</router-link>
    <ul class="nav-links">
      <li>
        <router-link to="/about" class="nav-link" exact-active-class="active">ABOUT</router-link>
      </li>
      <li>
        <router-link to="/expertise" class="nav-link" exact-active-class="active">EXPERTISE</router-link>
      </li>
      <li>
        <router-link to="/contact" class="nav-link" exact-active-class="active">CONTACT</router-link>
      </li>
    </ul>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted, watch } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()

const isBlackPage = ref(false)
const isScrolled = ref(false)

const updateNavbarStyle = () => {
  // Always black on /expertise and /contact
  isBlackPage.value = ['/expertise', '/contact'].includes(route.path)
}

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50
}

onMounted(() => {
  updateNavbarStyle()
  handleScroll()
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

// Watch for route changes
watch(route, () => {
  updateNavbarStyle()
})
</script>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  padding: 1.25rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  z-index: 10;
  transition: background-color 0.3s ease;
}

.navbar-black {
  background-color: black;
}

.logo {
  font-size: 1.5rem;
  font-weight: bold;
  color: white;
  letter-spacing: 1px;
  text-decoration: none;
}

.logo.active::after {
  display: none;
}

.nav-links {
  display: flex;
  gap: 1rem;
}

.nav-link {
  position: relative;
  color: white;
  text-decoration: none;
  font-weight: 600;
  font-size: 0.75rem;
  text-transform: uppercase;
  padding: 0 0.25rem;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -25px;
  left: 0;
  width: 100%;
  height: 3px;
  background-color: white;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.nav-link:hover::after {
  transform: scaleX(1);
}

.nav-link.active::after {
  transform: scaleX(1);
}
</style>
