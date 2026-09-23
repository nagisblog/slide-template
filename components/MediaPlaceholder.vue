<script setup lang="ts">
withDefaults(defineProps<{ src?: string; alt?: string; label?: string; fit?: 'cover' | 'contain' }>(), {
  alt: '', label: '画像・図版', fit: 'cover',
})
</script>

<template>
  <div class="media-placeholder" :class="{ 'has-image': src }">
    <img v-if="src" :src="src" :alt="alt" :style="{ objectFit: fit }" />
    <slot v-else><span>{{ label }}</span></slot>
  </div>
</template>
