<script setup lang="ts">
import Button from 'primevue/button'
import { computed } from 'vue'
import { useI18n } from 'vue-i18n'
import { getFlagEmoji, type SUPPORTED_LANGUAGES, SupportedLanguages } from '@/services/i18n'
import { useRouter } from 'vue-router'
import WorldAnimation from '@/components/WorldAnimation.vue'

const { t, locale } = useI18n()

const router = useRouter()

const howToPlayKeys = computed(() => [
  '1',
  '2',
  '3',
  '4',
  '5',
  '6',
  '7',
  '8',
  '9',
  '10',
  '11',
  '12',
  '13',
  '14',
])

function onLanguageChange(language: SUPPORTED_LANGUAGES) {
  locale.value = language
  router.push({ name: 'welcome', params: { language } })
}
</script>

<template>
  <main class="mb-4 px-4 mx-auto max-w-3xl">
    <section class="my-40 md:my-15 text-center">
      <p class="text-yellow-400 uppercase tracking-wide text-sm mb-1">
        BIT Culture Festival 2025 · Sri Lankan Booth
      </p>
      <h1 class="text-center text-4xl sm:text-6xl">
        {{ t('pages.welcome.title') }}
      </h1>
      <p class="mt-2 text-gray-400">
        {{ t('pages.welcome.subtitle') }}
        <span class="text-yellow-400 font-semibold">
          {{ t('pages.welcome.rules-hint') }}
        </span>
      </p>

      <div class="my-4">
        <h2 class="text-sm text-gray-400">
          {{ t('pages.welcome.choose-language') }}
        </h2>

        <div class="flex justify-center mt-2 gap-2">
          <Button asChild link v-slot="slotProps">
            <RouterLink
              :to="{ name: 'welcome', params: { language: SupportedLanguages.pt } }"
              :class="[slotProps.class, 'text-2xl']"
              @click.prevent="() => onLanguageChange(SupportedLanguages.pt)"
            >
              {{ getFlagEmoji(SupportedLanguages.pt) }}
            </RouterLink>
          </Button>
          <Button asChild link v-slot="slotProps">
            <RouterLink
              :to="{ name: 'welcome', params: { language: SupportedLanguages.en } }"
              :class="[slotProps.class, 'text-2xl']"
              @click.prevent="() => onLanguageChange(SupportedLanguages.en)"
            >
              {{ getFlagEmoji(SupportedLanguages.en) }}
            </RouterLink>
          </Button>
          <Button asChild link v-slot="slotProps">
            <RouterLink
              :to="{ name: 'welcome', params: { language: SupportedLanguages.es } }"
              :class="[slotProps.class, 'text-2xl']"
              @click.prevent="() => onLanguageChange(SupportedLanguages.es)"
            >
              {{ getFlagEmoji(SupportedLanguages.es) }}
            </RouterLink>
          </Button>
          <Button asChild link v-slot="slotProps">
            <RouterLink
              :to="{ name: 'welcome', params: { language: SupportedLanguages.de } }"
              :class="[slotProps.class, 'text-2xl']"
              @click.prevent="() => onLanguageChange(SupportedLanguages.de)"
            >
              {{ getFlagEmoji(SupportedLanguages.de) }}
            </RouterLink>
          </Button>
          <Button asChild link v-slot="slotProps">
            <RouterLink
              :to="{ name: 'welcome', params: { language: SupportedLanguages.zh } }"
              :class="[slotProps.class, 'text-2xl']"
              @click.prevent="() => onLanguageChange(SupportedLanguages.zh)"
            >
              {{ getFlagEmoji(SupportedLanguages.zh) }}
            </RouterLink>
          </Button>
        </div>
      </div>

      <div
        class="aspect-video border border-gray-200 grid place-items-center mb-8 mt-4 rounded-xl text-xl w-full p-8"
      >
        <WorldAnimation />
      </div>

      <div class="flex justify-center">
        <Button asChild v-slot="slotProps">
          <RouterLink :to="{ name: 'game' }" :class="slotProps.class">
            {{ t('common.new-game') }}
          </RouterLink>
        </Button>
      </div>
    </section>

    <section class="mx-auto max-w-md my-10">
      <h2 class="text-center text-2xl">{{ t('pages.welcome.how-to-play.title') }}</h2>

      <div class="mt-2 rounded bg-zinc-800 p-4">
        <ol class="list-disc space-y-2 pl-4">
          <li v-for="key in howToPlayKeys" :key="key">
            {{ t(`pages.welcome.how-to-play.list.${key}`) }}
          </li>
        </ol>
      </div>
    </section>

    <section class="mx-auto max-w-3xl my-10 text-center">
      <Button asChild v-slot="slotProps">
        <RouterLink
          :to="{ name: 'about', params: { language: locale } }"
          :class="slotProps.class"
          class="inline-flex items-center gap-2 rounded-full border border-gray-200 px-4 py-2 text-sm text-black bg-white transition hover:border-white hover:bg-white/80"
        >
          About Us
        </RouterLink>
      </Button>
    </section>
  </main>
</template>
