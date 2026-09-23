<script setup lang="ts">
defineProps<{ image?: string; imageAlt?: string }>()
</script>

<template>
  <div class="slidev-layout sage-section">
    <MediaPlaceholder class="section-media" :src="image" :alt="imageAlt" />
    <div class="section-frame"><slot /></div>
  </div>
</template>
