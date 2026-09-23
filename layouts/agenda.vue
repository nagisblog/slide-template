<script setup lang="ts">
defineProps<{ image?: string; imageAlt?: string }>()
</script>

<template>
  <div class="slidev-layout sage-agenda">
    <main><slot /></main>
    <MediaPlaceholder class="agenda-media" :src="image" :alt="imageAlt" />
    <DeckFooter />
  </div>
</template>
