<script setup lang="ts">
const src = computed(() => {
  const base = import.meta.env.BASE_URL
  const path = '/images/hamster-geometric.png'
  return base && base !== '/' ? base.replace(/\/$/, '') + path : path
})
</script>

<template>
  <img class="hamster-mark" :src="src" alt="" aria-hidden="true" />
</template>
