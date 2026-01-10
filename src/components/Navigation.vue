<script setup lang="ts">
import { ref } from 'vue'
import { Menu, Github, Linkedin, Mail } from 'lucide-vue-next'

const isMenuOpen = ref(false)

function scrollToSection(id: string) {
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
    isMenuOpen.value = false
  }
}
</script>

<template>
  <nav
    class="fixed top-0 left-0 right-0 z-50 bg-white/80 backdrop-blur-md border-b border-gray-200"
  >
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        <!-- Logo -->
        <button
          type="button"
          @click="scrollToSection('home')"
          class="text-xl font-bold text-gray-900 hover:text-blue-600 transition-colors"
        >
          HJ
        </button>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center gap-8">
          <button
            type="button"
            @click="scrollToSection('home')"
            class="text-gray-600 hover:text-blue-600 transition-colors"
          >
            Home
          </button>
          <button
            type="button"
            @click="scrollToSection('projects')"
            class="text-gray-600 hover:text-blue-600 transition-colors"
          >
            Projects
          </button>
          <button
            type="button"
            @click="scrollToSection('about')"
            class="text-gray-600 hover:text-blue-600 transition-colors"
          >
            About
          </button>
          <button
            type="button"
            @click="scrollToSection('contact')"
            class="px-6 py-2 bg-blue-600 text-white rounded-full hover:bg-blue-700 transition-colors"
          >
            Contact
          </button>
        </div>

        <!-- Social Icons - Desktop -->
        <div class="hidden md:flex items-center gap-4">
          <a
            href="https://github.com"
            target="_blank"
            rel="noopener noreferrer"
            class="text-gray-600 hover:text-blue-600 transition-colors"
            aria-label="GitHub"
          >
            <Github class="w-5 h-5" />
          </a>
          <a
            href="https://linkedin.com"
            target="_blank"
            rel="noopener noreferrer"
            class="text-gray-600 hover:text-blue-600 transition-colors"
            aria-label="LinkedIn"
          >
            <Linkedin class="w-5 h-5" />
          </a>
          <a
            href="mailto:hello@example.com"
            class="text-gray-600 hover:text-blue-600 transition-colors"
            aria-label="Email"
          >
            <Mail class="w-5 h-5" />
          </a>
        </div>

        <!-- Mobile Menu Button -->
        <button
          type="button"
          @click="isMenuOpen = !isMenuOpen"
          class="md:hidden text-gray-600 hover:text-blue-600 transition-colors"
          aria-label="Toggle menu"
        >
          <Menu class="w-6 h-6" />
        </button>
      </div>

      <!-- Mobile Menu -->
      <div v-if="isMenuOpen" class="md:hidden py-4 border-t border-gray-200">
        <div class="flex flex-col gap-4">
          <button
            type="button"
            @click="scrollToSection('home')"
            class="text-gray-600 hover:text-blue-600 transition-colors text-left"
          >
            Home
          </button>
          <button
            type="button"
            @click="scrollToSection('projects')"
            class="text-gray-600 hover:text-blue-600 transition-colors text-left"
          >
            Projects
          </button>
          <button
            type="button"
            @click="scrollToSection('about')"
            class="text-gray-600 hover:text-blue-600 transition-colors text-left"
          >
            About
          </button>
          <button
            type="button"
            @click="scrollToSection('contact')"
            class="text-gray-600 hover:text-blue-600 transition-colors text-left"
          >
            Contact
          </button>
          <div class="flex items-center gap-4 pt-4 border-t border-gray-200">
            <a
              href="https://github.com/jamoul-hussein"
              target="_blank"
              rel="noopener noreferrer"
              class="text-gray-600 hover:text-blue-600 transition-colors"
              aria-label="GitHub"
            >
              <Github class="w-5 h-5" />
            </a>
            <a
              href="https://de.linkedin.com/in/hussein-jamoul-98828a1aa"
              target="_blank"
              rel="noopener noreferrer"
              class="text-gray-600 hover:text-blue-600 transition-colors"
              aria-label="LinkedIn"
            >
              <Linkedin class="w-5 h-5" />
            </a>
            <a
              href="mailto:hello@example.com"
              class="text-gray-600 hover:text-blue-600 transition-colors"
              aria-label="Email"
            >
              <Mail class="w-5 h-5" />
            </a>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>


