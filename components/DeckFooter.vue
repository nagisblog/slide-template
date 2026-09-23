<template>
  <footer v-if="$frontmatter.footer !== false" class="deck-footer">
    <span>{{ $frontmatter.footer || $slidev.configs.title }}</span>
    <span>{{ $slidev.nav.currentPage }}</span>
  </footer>
</template>
