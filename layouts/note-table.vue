<template>
  <div class="slidev-layout sage-default">
    <header><slot name="title" /></header>
    <main class="table-with-note"><div><slot name="note" /></div><div><slot name="table" /></div></main>
    <DeckFooter />
  </div>
</template>
