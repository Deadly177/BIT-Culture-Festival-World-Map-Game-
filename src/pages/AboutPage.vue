<script setup lang="ts">
import { useI18n } from 'vue-i18n'
const { t } = useI18n()
</script>

<template>
  <main class="px-4 mx-auto max-w-3xl my-10 space-y-6">
    <header class="text-center space-y-2">
      <h1 class="text-3xl font-semibold text-yellow-400">{{ t('pages.about.title') }}</h1>
      <p class="text-gray-400">{{ t('pages.about.subtitle') }}</p>
    </header>

    <section class="rounded-lg border border-yellow-400 bg-(--p-inputtext-background) p-4 text-left space-y-3">
      <p>{{ t('pages.about.paragraph1') }}</p>
      <p>{{ t('pages.about.paragraph2') }}</p>
      <p>{{ t('pages.about.paragraph3') }}</p>
      <div class="font-semibold space-y-1">
        <div>{{ t('pages.about.signature.name') }}</div>
        <div>{{ t('pages.about.signature.role') }}</div>
        <div>{{ t('pages.about.signature.title') }}</div>
      </div>
    </section>
  </main>
</template>
