<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<template>
  <footer class="bg-gray-900 text-white py-12">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
      <div class="flex flex-col md:flex-row items-center justify-between gap-4">
        <div class="text-center md:text-left">
          <div class="text-2xl font-bold mb-2">Hussein Jamoul</div>
          <p class="text-gray-400">Web Developer & Designer</p>
        </div>

        <div class="text-center md:text-right text-gray-400">
          <p>© {{ year }} Hussein Jamoul. All rights reserved.</p>
          <p class="text-sm mt-1">Built with Vue & Tailwind CSS</p>
        </div>
      </div>
    </div>
  </footer>
</template>


