<template>
  <div class="slidev-layout sage-default">
    <header><slot name="title" /></header>
    <main class="code-explanation"><div><slot name="code" /></div><div><slot name="explanation" /></div></main>
    <DeckFooter />
  </div>
</template>
