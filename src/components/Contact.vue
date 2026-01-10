<script setup lang="ts">
import { reactive, ref } from 'vue'
import { Mail, Github, Linkedin, Lock } from 'lucide-vue-next'
import emailjs from '@emailjs/browser'

const formData = reactive({
  name: '',
  email: '',
  message: '',
})

const isSubmitting = ref(false)
const submitError = ref<string | null>(null)
const submitSuccess = ref(false)

// Toggle this when you want to re-enable the form.
const isFormEnabled = ref(false)

async function handleSubmit() {
  if (!isFormEnabled.value) {
    submitSuccess.value = false
    submitError.value = 'The contact form is currently disabled. Please email me directly instead.'
    return
  }

  submitError.value = null
  submitSuccess.value = false

  const serviceId = import.meta.env.VITE_EMAILJS_SERVICE_ID as string | undefined
  const templateId = import.meta.env.VITE_EMAILJS_TEMPLATE_ID as string | undefined
  const publicKey = import.meta.env.VITE_EMAILJS_PUBLIC_KEY as string | undefined

  if (!serviceId || !templateId || !publicKey) {
    submitError.value =
      'Email sending is not configured yet. Please set VITE_EMAILJS_SERVICE_ID, VITE_EMAILJS_TEMPLATE_ID, and VITE_EMAILJS_PUBLIC_KEY.'
    return
  }

  isSubmitting.value = true
  try {
    await emailjs.send(
      serviceId,
      templateId,
      {
        to_name: 'Hussein Jamoul',
        to_email: 'jamoulh312@gmail.com',
        from_name: formData.name,
        reply_to: formData.email,
        message: formData.message,
      },
      { publicKey },
    )

    submitSuccess.value = true
    formData.name = ''
    formData.email = ''
    formData.message = ''
  } catch (err) {
    submitError.value =
      err instanceof Error ? err.message : 'Failed to send message. Please try again later.'
  } finally {
    isSubmitting.value = false
  }
}
</script>

<template>
  <section id="contact" class="py-24 bg-white">
    <div class="max-w-7xl mx-auto px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center space-y-4 mb-16">
        <h2 class="text-4xl md:text-6xl font-bold text-gray-900">
          Get In
          <span class="bg-gradient-to-r from-blue-600 to-purple-600 bg-clip-text text-transparent">
            Touch
          </span>
        </h2>
        <p class="text-xl text-gray-600 max-w-2xl mx-auto">
          Have a project in mind? Let's work together to create something amazing
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
        <!-- Contact Info -->
        <div class="space-y-8">
          <div>
            <h3 class="text-2xl font-bold text-gray-900 mb-4">Let's talk about your project</h3>
            <p class="text-gray-600 leading-relaxed">
              I'm always interested in hearing about new projects and opportunities. Whether you
              have a question or just want to say hi, feel free to reach out!
            </p>
          </div>

          <!-- Contact Methods -->
          <div class="space-y-4">
            <a
              href="mailto:jamoulh312@gmail.com"
              class="flex items-center gap-4 p-4 bg-gray-50 rounded-xl hover:bg-blue-50 transition-colors group"
            >
              <div
                class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-blue-600 group-hover:bg-blue-600 group-hover:text-white transition-colors"
              >
                <Mail class="w-6 h-6" />
              </div>
              <div>
                <div class="font-semibold text-gray-900">Email</div>
                <div class="text-gray-600">jamoulh312@gmail.com</div>
              </div>
            </a>

            <a
              href="https://github.com/jamoul-hussein"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center gap-4 p-4 bg-gray-50 rounded-xl hover:bg-blue-50 transition-colors group"
            >
              <div
                class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-blue-600 group-hover:bg-blue-600 group-hover:text-white transition-colors"
              >
                <Github class="w-6 h-6" />
              </div>
              <div>
                <div class="font-semibold text-gray-900">GitHub</div>
                <div class="text-gray-600">github.com/jamoul-hussein</div>
              </div>
            </a>

            <a
              href="https://linkedin.com/in/hussein-jamoul-98828a1aa"
              target="_blank"
              rel="noopener noreferrer"
              class="flex items-center gap-4 p-4 bg-gray-50 rounded-xl hover:bg-blue-50 transition-colors group"
            >
              <div
                class="w-12 h-12 bg-white rounded-full flex items-center justify-center text-blue-600 group-hover:bg-blue-600 group-hover:text-white transition-colors"
              >
                <Linkedin class="w-6 h-6" />
              </div>
              <div>
                <div class="font-semibold text-gray-900">LinkedIn</div>
                <div class="text-gray-600">linkedin.com/in/hussein-jamoul-98828a1aa</div>
              </div>
            </a>
          </div>
        </div>

        <!-- Contact Form -->
        <div class="relative bg-gradient-to-br from-blue-50 to-purple-50 p-8 rounded-2xl overflow-hidden">
          <!-- "Disabled" overlay -->
          <div
            v-if="!isFormEnabled"
            class="absolute inset-0 z-10 flex items-center justify-center p-6 bg-white/55 backdrop-blur-sm"
          >
            <div class="max-w-md w-full rounded-2xl border border-gray-200 bg-white/80 shadow-sm p-6 text-center">
              <div class="mx-auto mb-3 inline-flex h-12 w-12 items-center justify-center rounded-full bg-gray-900 text-white">
                <Lock class="h-6 w-6" />
              </div>
              <div class="text-lg font-semibold text-gray-900">Contact form disabled</div>
              <p class="mt-2 text-sm text-gray-600">
                Please email me directly at
                <a class="font-semibold text-blue-700 hover:underline" href="mailto:jamoulh312@gmail.com">
                  jamoulh312@gmail.com
                </a>
              </p>
            </div>
          </div>

          <form
            class="space-y-6"
            :class="!isFormEnabled ? 'grayscale opacity-70 pointer-events-none select-none' : ''"
            @submit.prevent="handleSubmit"
            :aria-disabled="!isFormEnabled"
          >
            <div v-if="submitSuccess" class="rounded-xl bg-green-50 text-green-800 px-4 py-3">
              Thanks! Your message has been sent.
            </div>
            <div v-else-if="submitError" class="rounded-xl bg-red-50 text-red-800 px-4 py-3">
              {{ submitError }}
            </div>

            <div>
              <label for="name" class="block text-sm font-semibold text-gray-900 mb-2">Name</label>
              <input
                id="name"
                v-model="formData.name"
                type="text"
                name="name"
                required
                :disabled="!isFormEnabled || isSubmitting"
                class="w-full px-4 py-3 bg-white border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-600 focus:border-transparent transition-all"
                placeholder="Your name"
              />
            </div>

            <div>
              <label for="email" class="block text-sm font-semibold text-gray-900 mb-2">Email</label>
              <input
                id="email"
                v-model="formData.email"
                type="email"
                name="email"
                required
                :disabled="!isFormEnabled || isSubmitting"
                class="w-full px-4 py-3 bg-white border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-600 focus:border-transparent transition-all"
                placeholder="your@email.com"
              />
            </div>

            <div>
              <label for="message" class="block text-sm font-semibold text-gray-900 mb-2">
                Message
              </label>
              <textarea
                id="message"
                v-model="formData.message"
                name="message"
                required
                rows="5"
                :disabled="!isFormEnabled || isSubmitting"
                class="w-full px-4 py-3 bg-white border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-600 focus:border-transparent transition-all resize-none"
                placeholder="Tell me about your project..."
              />
            </div>

            <button
              type="submit"
              :disabled="!isFormEnabled || isSubmitting"
              class="w-full px-8 py-4 bg-blue-600 text-white rounded-xl font-semibold hover:bg-blue-700 transition-all hover:scale-105 shadow-lg shadow-blue-200"
            >
              {{ isSubmitting ? 'Sending…' : 'Send Message' }}
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>


