<script setup lang="ts">
import { onMounted, onUnmounted, ref } from 'vue'
import lottie, { type AnimationItem } from 'lottie-web'

const containerRef = ref<HTMLDivElement | null>(null)
let animation: AnimationItem | null = null

onMounted(() => {
  if (!containerRef.value) return

  animation = lottie.loadAnimation({
    container: containerRef.value,
    renderer: 'svg',
    loop: true,
    autoplay: true,
    path: '/animations/world.json',
    rendererSettings: {
      preserveAspectRatio: 'xMidYMid meet',
    },
  })
})

onUnmounted(() => {
  animation?.destroy()
})
</script>

<template>
  <div class="w-full flex justify-center" aria-hidden="true">
    <div class="max-w-[420px] w-full" ref="containerRef" />
  </div>
</template>
