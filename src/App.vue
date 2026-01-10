<template>
  <div class="min-h-screen bg-white">
    <Navigation />
    <main>
      <Hero />
      <Portfolio />
      <About />
      <Contact />
    </main>
    <Footer />
  </div>
</template>
<script setup lang="ts">
import Navigation from './components/Navigation.vue'
import Hero from './components/Hero.vue'
import Portfolio from './components/Portfolio.vue'
import About from './components/About.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
</script>
