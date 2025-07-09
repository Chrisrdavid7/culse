<!-- src/App.vue -->
<template>
    <Navbar :scrolledToQuote="scrolledToQuote" />

  <div>
    <router-view :onQuoteScrollChange="handleScrollChange" />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import Navbar from './components/Navbar.vue'

window.addEventListener('beforeunload', () => {
  localStorage.setItem('scrollY', window.scrollY)

  const scrolledToQuote = ref(false)

// This function will be called from children pages
function handleScrollChange(val) {
  scrolledToQuote.value = val
}
})

</script>
