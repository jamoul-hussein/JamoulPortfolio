<script setup lang="ts">
import { Code } from 'lucide-vue-next'

function scrollToProjects() {
  const element = document.getElementById('projects')
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' })
  }
}
</script>

<template>
  <section
    id="home"
    class="min-h-screen flex items-center justify-center bg-gradient-to-br from-gray-50 to-blue-50 pt-16"
  >
    <div class="max-w-7xl mx-auto px-6 lg:px-8 py-20">
      <div class="flex flex-col lg:flex-row items-center gap-12 lg:gap-16">
        <!-- Personal Photo -->
        <div class="flex-shrink-0">
          <div class="relative">
            <div
              class="w-64 h-64 md:w-80 md:h-80 rounded-full overflow-hidden border-8 border-white shadow-2xl"
            >
              <img
                src="/src/assets/MyPortfolio.jpg"
                alt="Hussein Jamoul - Full-Stack Web Developer"
                class="w-full h-full object-cover"
              />
            </div>
            <!-- Decorative elements -->
            <div
              class="absolute -top-4 -right-4 w-24 h-24 bg-blue-200 rounded-full blur-2xl opacity-60"
            />
            <div
              class="absolute -bottom-4 -left-4 w-32 h-32 bg-purple-200 rounded-full blur-2xl opacity-60"
            />
          </div>
        </div>

        <!-- Content -->
        <div class="flex-1 text-center lg:text-left space-y-8">
          <!-- Icon - Hidden on larger screens since we have photo -->
          <div
            class="inline-flex items-center justify-center w-20 h-20 rounded-full bg-blue-100 text-blue-600 mb-4 lg:hidden"
          >
            <Code class="w-10 h-10" />
          </div>

          <!-- Main Heading -->
          <h1 class="text-5xl md:text-7xl font-bold text-gray-900 tracking-tight">
            Hi, I'm
            <span class="bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
              Hussein Jamoul
            </span>
          </h1>

          <!-- Subtitle -->
          <p class="text-xl md:text-2xl text-gray-600 max-w-3xl lg:mx-0 mx-auto">
            A passionate
            <span class="text-blue-600 font-semibold">Web Developer</span>
            crafting beautiful, accessible, and performant digital experiences
          </p>

          <!-- Description -->
          <p class="text-lg text-gray-500 max-w-2xl lg:mx-0 mx-auto leading-relaxed">
            I specialize in building modern web applications with Svelte , SvelteKit, Vue, Vue3, TypeScript, Tailwind CSS, Node.js, 
            PostgreSQL, MySQL, MongoDB, REST API, AWS, Docker, Kubernetes, PHP, Laravel, Symfony, WordPress and cutting-edge
            technologies. With a keen eye for design and a commitment to clean code, I bring ideas to
            life on the web.
          </p>

          <!-- CTA Buttons -->
          <div
            class="flex flex-col sm:flex-row items-center lg:justify-start justify-center gap-4 pt-8"
          >
            <button
              type="button"
              @click="scrollToProjects"
              class="px-8 py-4 bg-blue-600 text-white rounded-full font-semibold hover:bg-blue-700 transition-all hover:scale-105 shadow-lg shadow-blue-200"
            >
              View My Work
            </button>
            <a
              href="#contact"
              class="px-8 py-4 bg-white text-gray-900 rounded-full font-semibold hover:bg-gray-50 transition-all border-2 border-gray-200 hover:border-blue-600"
            >
              Get In Touch
            </a>
          </div>

          <!-- Stats -->
          <div class="grid grid-cols-3 gap-8 max-w-2xl lg:mx-0 mx-auto pt-16">
            <div>
              <div class="text-4xl font-bold text-gray-900">10+</div>
              <div class="text-sm text-gray-600 mt-1">Projects Completed</div>
            </div>
            <div>
              <div class="text-4xl font-bold text-gray-900">5+</div>
              <div class="text-sm text-gray-600 mt-1">Years Experience</div>
            </div>
            <div>
              <div class="text-4xl font-bold text-gray-900">3+</div>
              <div class="text-sm text-gray-600 mt-1">Happy Companies</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>


