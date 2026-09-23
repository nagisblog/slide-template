<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(defineProps<{ src?: string; alt?: string; label?: string; fit?: 'cover' | 'contain' }>(), {
  alt: '', label: '画像・図版', fit: 'cover',
})

const resolvedSrc = computed(() => {
  if (!props.src) return undefined
  const base = import.meta.env.BASE_URL
  if (base && base !== '/' && props.src.startsWith('/')) {
    return base.replace(/\/$/, '') + props.src
  }
  return props.src
})
</script>

<template>
  <div class="media-placeholder" :class="{ 'has-image': src }">
    <img v-if="resolvedSrc" :src="resolvedSrc" :alt="alt" :style="{ objectFit: fit }" />
    <slot v-else><span>{{ label }}</span></slot>
  </div>
</template>
