<!-- My AI essays, each with a QR code that people can photograph. The QR images are in public/qr -->
<script setup lang="ts">
const base = import.meta.env.BASE_URL
const essays = [
  ['universities-and-ai', 'The University In The AI Era', 'What AI means for universities and CS programs, and the changes I am making'],
  ['yes-and', 'Yes, And...', 'Should you still become a programmer? Yes, and build skills beyond writing code'],
  ['working-with-ai', 'Working With AI: A Concrete Example', 'A real parser bug: what the AI got right, and the wrong fixes it proposed'],
  ['code-is-cheap', 'Code is Cheap(er)', 'Code got cheaper to create, but understanding it did not, and complexity is still the enemy'],
]
</script>

<template>
  <div class="essays">
    <div v-for="[slug, title, about] in essays" :key="slug" class="essay">
      <img :src="`${base}qr/${slug}.png`" :alt="`QR code for ${title}`">
      <div>
        <a :href="`https://htmx.org/essays/${slug}/`">{{ title }}</a>
        <p>{{ about }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.essays {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem 2.5rem;
  margin-top: 2.25rem;
}

.essay {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.essay img {
  width: 7.25rem;
  flex-shrink: 0;
  background: #fff;
  border-radius: 4px;
  image-rendering: pixelated;
}

.essay a {
  font-family: var(--serif);
  font-size: 1.55rem;
  font-weight: 600;
  line-height: 1.2;
  color: #dfe9ff;
  border: 0;
}

.essay p {
  margin: 0.4rem 0 0;
  font-size: 1.25rem;
  line-height: 1.3;
  color: #fff;
}
</style>
