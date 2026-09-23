<script setup lang="ts">
defineProps<{ image?: string; imageAlt?: string }>()
</script>

<template>
  <div class="slidev-layout sage-cover">
    <MediaPlaceholder class="cover-media" :src="image" :alt="imageAlt" />
    <div class="cover-frame"><slot /></div>
  </div>
</template>
