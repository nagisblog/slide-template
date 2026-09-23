<template>
  <div class="slidev-layout sage-default">
    <header><slot name="title" /></header>
    <main class="columns columns-three"><div><slot name="first" /></div><div><slot name="second" /></div><div><slot name="third" /></div></main>
    <DeckFooter />
  </div>
</template>
