<script setup lang="ts">
import { useLanguage } from '@/composables/LangKey'

const { currentLang } = useLanguage()
</script>

<template>
  <button
    class="bg-blue-700 hover:bg-blue-600 text-white px-8 py-3 rounded-md font-semibold transition-all"
  >
    <a v-if="currentLang === 'en'" href="/CV ENG.pdf" download="CV.pdf" target="_blank"
      >Download CV</a
    >
    <a v-else href="/CV FR.pdf" download="CV.pdf" target="_blank">Télécharger CV</a>
  </button>
</template>
