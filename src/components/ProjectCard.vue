<script setup lang="ts">
import { ExternalLink } from 'lucide-vue-next'

defineProps<{
  title: string
  description: string
  image: string
  tags: string[]
  link?: string
}>()
</script>

<template>
  <div
    class="group relative bg-white rounded-2xl overflow-hidden shadow-md hover:shadow-2xl transition-all duration-300 hover:-translate-y-2"
  >
    <!-- Image -->
    <div class="relative h-64 overflow-hidden bg-gray-100">
      <img
        :src="image"
        :alt="title"
        class="w-full h-full object-cover transition-transform duration-500 group-hover:scale-110"
      />
      <!-- Overlay on hover -->
      <div
        class="absolute inset-0 bg-gradient-to-t from-black/60 via-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-end justify-center pb-6"
      >
        <a
          v-if="link"
          :href="link"
          target="_blank"
          rel="noopener noreferrer"
          class="px-6 py-3 bg-white text-gray-900 rounded-full font-semibold hover:bg-blue-600 hover:text-white transition-colors flex items-center gap-2"
        >
          View Project
          <ExternalLink class="w-4 h-4" />
        </a>
      </div>
    </div>

    <!-- Content -->
    <div class="p-6 space-y-4">
      <h3 class="text-2xl font-bold text-gray-900 group-hover:text-blue-600 transition-colors">
        {{ title }}
      </h3>
      <p class="text-gray-600 leading-relaxed">
        {{ description }}
      </p>

      <!-- Tags -->
      <div class="flex flex-wrap gap-2 pt-2">
        <span
          v-for="(tag, index) in tags"
          :key="index"
          class="px-3 py-1 text-sm bg-blue-50 text-blue-700 rounded-full font-medium"
        >
          {{ tag }}
        </span>
      </div>
    </div>

    <!-- Accent line -->
    <div
      class="absolute top-0 left-0 right-0 h-1 bg-gradient-to-r from-blue-600 to-purple-600 transform scale-x-0 group-hover:scale-x-100 transition-transform duration-300"
    />
  </div>
</template>


