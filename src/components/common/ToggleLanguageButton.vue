<script setup lang="ts">
import { useLanguage } from '@/composables/LangKey'

const { currentLang, toggleLang } = useLanguage()
</script>
<template>
  <div class="fixed top-6 md:right-8 right-4 z-50">
    <div
      class="relative flex items-center p-1 rounded-full bg-white/5 backdrop-blur-md border border-white/10 shadow-lg min-w-fit whitespace-nowrap"
    >
      <!-- Active Indicator -->
      <div
        class="absolute top-1 bottom-1 w-1/2 rounded-full bg-white/15 transition-all duration-300 ease-in-out"
        :class="currentLang === 'en' ? 'left-1' : 'left-1/2'"
      ></div>

      <!-- EN -->
      <button
        @click="toggleLang"
        class="relative z-10 px-4 py-1.5 text-sm font-medium transition-colors duration-200"
        :class="currentLang === 'en' ? 'text-blue-500' : 'text-white/50 hover:text-white/80'"
      >
        EN
      </button>

      <!-- FR -->
      <button
        @click="toggleLang"
        class="relative z-10 px-4 py-1.5 text-sm font-medium transition-colors duration-200"
        :class="currentLang === 'fr' ? 'text-blue-500' : 'text-white/50 hover:text-white/80'"
      >
        FR
      </button>
    </div>
  </div>
</template>
