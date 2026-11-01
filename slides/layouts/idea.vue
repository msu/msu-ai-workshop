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
    <div class="eyebrow">Big Idea {{ n }}</div>
    <slot />
  </div>
</template>

<style scoped>
.idea {
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 5rem;
}

.idea :deep(h1) {
  font-size: 3.4rem;
  line-height: 1.1;
}

.idea :deep(h2) {
  font-family: var(--serif);
  font-style: italic;
  font-weight: 400;
  font-size: 1.5rem;
  color: var(--muted);
  margin-top: 0.75rem;
}
</style>
