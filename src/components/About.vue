<script setup lang="ts">
import type { Component } from 'vue'
import { Code, Palette, Smartphone } from 'lucide-vue-next'

type Skill = {
  icon: Component
  title: string
  description: string
  items: string[]
}

const skills: Skill[] = [
  {
    icon: Code,
    title: 'Development',
    description:
      'Expert in Svelte, SvelteKit, Vue, Vue3, TypeScript, PHP, Laravel, Symfony, WordPress, Tailwind CSS, Node.js, MariaDB, MySQL, MongoDB, REST API, AWS, Docker, Kubernetes, and modern web technologies. Building scalable and maintainable applications.',
    items: ['Svelte', 'SvelteKit', 'Vue', 'Vue3', 'TypeScript', 'PHP', 'Laravel', 'Symfony', 'WordPress', 'Tailwind CSS', 'Node.js', 'MariaDB', 'MySQL', 'MongoDB', 'REST API', 'AWS', 'Docker', 'Kubernetes'],
  },
  {
    icon: Palette,
    title: 'Design',
    description:
      'Creating intuitive user interfaces with attention to detail, accessibility, and modern design principles. Figma, Tailwind CSS, Animation.',
    items: ['UI/UX Design', 'Figma', 'Tailwind CSS', 'Animation', 'Boostrap', 'HTML', 'CSS', 'JavaScript', 'Dashboard Design', 'Admin Panel Design'],
  },
  {
    icon: Smartphone,
    title: 'Web',
    description:
      'Crafting seamless experiences across all devices with mobile-first approach and progressive enhancement. SEO, Analytics, Monitoring, Testing, Debugging, Deployment, CI/CD, DevOps, Cloud, Virtualization, Containerization.',
    items: ['Mobile-First', 'PWA', 'Performance', 'Accessibility', 'SEO', 'Analytics', 'Monitoring', 'Testing', 'Debugging', 'Deployment', 'CI/CD', 'DevOps', 'Cloud', 'Virtualization', 'Containerization', 'S3 ' ],
  },
]
</script>

<template>
  <section id="about" class="py-24 bg-gradient-to-br from-blue-50 to-purple-50">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center space-y-4 mb-16">
        <h2 class="text-4xl md:text-6xl font-bold text-gray-900">
          About
          <span class="bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
            Me
          </span>
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          Passionate about creating exceptional digital experiences
        </p>
      </div>

      <!-- Bio -->
      <div class="max-w-3xl mx-auto text-center mb-16">
        <p class="text-lg text-gray-700 leading-relaxed">
          With over 5 years of experience in web development, I've had the privilege of working with
          diverse clients and teams to bring innovative ideas to life. My approach combines
          technical expertise with creative problem-solving to deliver solutions that not only look
          great but perform exceptionally.
        </p>
      </div>

      <!-- Skills Grid -->
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div
          v-for="(skill, index) in skills"
          :key="index"
          class="bg-white p-8 rounded-2xl shadow-md hover:shadow-xl transition-all duration-300 hover:-translate-y-2"
        >
          <div
            class="inline-flex items-center justify-center w-16 h-16 rounded-full bg-blue-100 text-blue-600 mb-6"
          >
            <component :is="skill.icon" class="w-8 h-8" />
          </div>
          <h3 class="text-2xl font-bold text-gray-900 mb-4">
            {{ skill.title }}
          </h3>
          <p class="text-gray-600 mb-6 leading-relaxed">
            {{ skill.description }}
          </p>
          <ul class="space-y-2">
            <li v-for="(item, itemIndex) in skill.items" :key="itemIndex" class="flex items-center text-gray-700">
              <div class="w-1.5 h-1.5 rounded-full bg-blue-600 mr-3" />
              {{ item }}
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>


