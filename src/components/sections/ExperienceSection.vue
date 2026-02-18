<script setup lang="ts">
import jsonExpEn from '@data/en/experience.json'
import jsonExpFr from '@data/fr/experience.json'
import { computed } from 'vue'

import { useLanguage } from '@/composables/LangKey'

const { currentLang } = useLanguage()
interface Experience {
  title: string
  company: string
  city: string
  startDate: string
  endDate: string
  tasks: {
    keyword: string
    description: string
  }[]
}

const localJson = computed<Experience[]>(() => {
  return currentLang.value === 'fr' ? jsonExpFr : jsonExpEn
})
</script>

<template>
  <div>
    <div class="mb-16 text-center">
      <h2
        v-if="currentLang === 'en'"
        class="text-3xl md:text-4xl font-bold text-white tracking-tight uppercase"
      >
        Work <span class="text-blue-500">Experience</span>
      </h2>
      <h2 v-else class="text-3xl md:text-4xl font-bold text-white tracking-tight uppercase">
        <span class="text-blue-500">Expérience</span> Professionnelle
      </h2>
      <div class="h-1 w-20 bg-blue-600 mx-auto mt-4 rounded-full"></div>
    </div>

    <div class="space-y-16">
      <div
        class="absolute left-7.75 top-45 bottom-20 w-px bg-linear-to-b from-blue-500/50 via-white/10 to-transparent"
      ></div>
      <div v-for="item in localJson" :key="item.company" class="relative pl-16 group">
        <div class="absolute left-0 top-1.5 flex items-center justify-center">
          <div
            class="h-4 w-4 rounded-full bg-blue-600 border-4 border-slate-950 z-10 shadow-[0_0_15px_rgba(37,99,235,0.5)] transition-transform group-hover:scale-125"
          ></div>
          <div class="absolute h-8 w-8 rounded-full bg-blue-600/20 blur-sm"></div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-[160px_1fr] gap-4 md:gap-8">
          <div
            v-if="item.company == 'BPCE' && currentLang === 'en'"
            class="text-white font-medium pt-1 group-hover:text-blue-400 transition-colors"
          >
            2024 — Present
          </div>
          <div
            v-else-if="item.company == 'BPCE' && currentLang === 'fr'"
            class="text-white font-medium pt-1 group-hover:text-blue-400 transition-colors"
          >
            2024 — Présent
          </div>
          <div
            v-else-if="item.company == 'Tediber'"
            class="text-white font-medium pt-1 group-hover:text-blue-400 transition-colors"
          >
            2023 — 2024
          </div>
          <div
            v-else
            class="text-white font-medium pt-1 group-hover:text-blue-400 transition-colors"
          >
            2020 - 2023
          </div>

          <div class="space-y-4">
            <div>
              <h3 class="text-2xl font-bold text-white group-hover:text-blue-400 transition-colors">
                {{ item.title }} <span class="text-slate-500 font-light mx-2">•</span>
                <span class="text-white group-hover:text-blue-400 transition-colors">{{
                  item.company
                }}</span>
              </h3>
              <div class="text-slate-500 text-sm mt-1">
                {{ item.city }} <span class="mx-1">•</span> {{ item.startDate }} —
                {{ item.endDate }}
              </div>
            </div>

            <ul class="space-y-3">
              <li
                v-for="(value, index) in item.tasks"
                :key="index"
                class="relative pl-6 text-slate-200 leading-relaxed text-sm before:content-['•'] before:absolute before:left-0 before:text-blue-500/60"
              >
                <strong>{{ value.keyword }}</strong> : {{ value.description }}
              </li>
            </ul>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
