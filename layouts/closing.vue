<script setup lang="ts">
defineProps<{ image?: string; imageAlt?: string }>()
</script>

<template>
  <div class="slidev-layout sage-closing">
    <MediaPlaceholder class="closing-media" :src="image" :alt="imageAlt" />
    <main><slot /></main>
  </div>
</template>
