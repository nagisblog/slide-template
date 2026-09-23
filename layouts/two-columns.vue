<template>
  <div class="slidev-layout sage-default">
    <header><slot name="title" /></header>
    <main class="columns"><div><slot name="left" /></div><div><slot name="right" /></div></main>
    <DeckFooter />
  </div>
</template>
