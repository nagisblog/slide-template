<script setup lang="ts">
withDefaults(defineProps<{ image?: string; imageAlt?: string; side?: 'left' | 'right' }>(), { side: 'right' })
</script>

<template>
  <div class="slidev-layout sage-split" :class="`media-${side}`">
    <MediaPlaceholder class="split-media" :src="image" :alt="imageAlt"><slot name="media"><span>画像・図版</span></slot></MediaPlaceholder>
    <main><slot /></main>
    <DeckFooter />
  </div>
</template>
