<script setup lang="ts">
import ProjectCard from './ProjectCard.vue'

type Project = {
  title: string
  description: string
  image: string
  tags: string[]
  link?: string
}

const projects: Project[] = [
  {
    title: 'GranfineoAR',
    description:
      'A full-featured blog website for a company called Granfineo, it is a WordPress website that uses the Raw CSS and Elementor plugin for the design and the SEO plugin for the SEO.' +
      'the design is RTL (Right to Left) for the Arabic language. content are blogs about web and graphic design.',
    image:
      '/photos/GranfineoAR.png',
    tags: ['WordPress', 'PHP', 'MySQL', 'HTML', 'CSS', 'JavaScript', 'Plugins', 'Elementor', 'SEO', 'Social Media', 'Analytics', 'Blogs', 'Web Design', 'Graphic Design'],
    link: 'https://arabic.grafineo.net/',
  },
  {
    title: 'Granfineo English',
    description:
      'A full-featured blog website called Granfineo, it is a WordPress website that uses the Raw CSS and Elementor plugin for the design and the SEO plugin for the SEO.' +
      'content are blogs about web and graphic design.',
    image:
      '/photos/GranfineoEng.png',
    tags: ['WordPress', 'PHP', 'MySQL', 'HTML', 'CSS', 'JavaScript', 'Plugins', 'Elementor', 'SEO', 'Social Media', 'Analytics', 'Blogs', 'Web Design', 'Graphic Design', 'IONOS Hosting', 'WordPress Hosting'],
    link: 'https://www.grafineo.net/',
  },
  {
    title: 'Blosa Grafineo',
    description:
      'An advanced platform dedicated to being a wiki for influencers, powered by an intelligent search experience and rich filtering.' +
      ' It features influencer biographies and curated social media content.' +
      ' An admin panel is included to manage influencers, content, and site settings.' +
      ' Deployed manually on a Hetzner server with a domain registered on IONOS.' +
      ' Backend: Laravel (PHP) API. Frontend: SvelteKit + Tailwind CSS + TypeScript, with an advanced security layer.',
    image:
      '/photos/BoslaAR.png',
    tags: ['SvelteKit', 'Tailwind CSS', 'Typescript', 'Laravel', 'API', 'Security', 'Admin Panel', 'Hetzner Hosting', 'IONOS Domain', 'Advanced Search Engine', 'Filtering System', 'Influencer Wiki', 'PHP', 'Docker', 'Node.js', 'MariaDB', 'Redis'],
    link: 'https://bosla.grafineo.net',
  },
]
</script>

<template>
  <section id="projects" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center space-y-4 mb-16">
        <h2 class="text-4xl md:text-6xl font-bold text-gray-900">
          Featured
          <span class="bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
            Projects
          </span>
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          A selection of my recent work showcasing diverse skills and creative solutions
        </p>
      </div>

      <!-- Projects Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <ProjectCard v-for="(project, index) in projects" :key="index" v-bind="project" />
      </div>
    </div>
  </section>
</template>


