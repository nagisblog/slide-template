<script setup lang="ts">
withDefaults(defineProps<{ side?: 'left' | 'right' }>(), { side: 'left' })
</script>

<template>
  <div class="slidev-layout sage-side" :class="`title-${side}`">
    <header><slot name="title" /></header>
    <main><slot /></main>
    <DeckFooter />
  </div>
</template>
