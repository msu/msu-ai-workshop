<!-- Inline SVG of a text file in an editor tab. Pass the name and the lines -->
<script setup lang="ts">
const props = defineProps<{ name: string, lines: string[] }>()
const height = 72 + props.lines.length * 25
</script>

<template>
  <svg class="fig" :viewBox="`0 0 480 ${height}`" role="img" :aria-label="`The file ${name}`">
    <rect width="480" :height="height" rx="8" class="fig-bg" />
    <g transform="translate(16 16)">
      <rect width="448" :height="height - 32" rx="7" class="fig-card" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V28 Z" class="fig-bar" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H180 V28 Z" fill="#fff" />
      <text x="14" y="19" class="fig-tab">{{ name }}</text>
      <text v-for="(line, i) in lines" :key="i" x="16" :y="52 + i * 25" class="fig-mono">{{ line }}</text>
    </g>
  </svg>
</template>
