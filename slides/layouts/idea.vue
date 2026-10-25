<!--
  Divider for one big idea.

  ---
  layout: idea
  n: 1
  ---
  # Learn The Command Line
  ## One line subtitle
-->
<script setup lang="ts">
defineProps({
  n: { type: [Number, String], default: 1 },
})
</script>

<template>
  <div class="slidev-layout idea">
    <div class="idea-num">{{ String(n).padStart(2, '0') }}</div>
    <div class="idea-body">
      <div class="eyebrow">Big Idea {{ n }}</div>
      <slot />
    </div>
  </div>
</template>

<style scoped>
.idea {
  height: 100%;
  display: grid;
  grid-template-columns: auto 1fr;
  align-items: center;
  column-gap: 3rem;
  padding: 0 4rem;
}

.idea-num {
  font-family: var(--mono);
  font-size: 9rem;
  line-height: 1;
  color: transparent;
  -webkit-text-stroke: 2px var(--msu-gold);
  text-shadow: 0 0 40px var(--glow);
}

.idea-body :deep(h1) {
  font-size: 3.2rem;
  line-height: 1.1;
}

.idea-body :deep(h2) {
  color: var(--muted);
  font-weight: 400;
  font-size: 1.4rem;
  margin-top: 0.75rem;
}
</style>
