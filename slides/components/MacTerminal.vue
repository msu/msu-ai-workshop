<!-- Inline SVG of a dark macOS Terminal window on a white panel -->
<script setup lang="ts">
defineProps({
  title: { type: String, default: 'my-course -- claude -- 80x24' },
  lines: {
    type: Array,
    default: () => [
      ['muted', 'Last login: Wed Nov  4 11:58:02 on ttys000'],
      ['', 'faculty@macbook ~ % cd courses/my-course'],
      ['', 'faculty@macbook my-course % claude'],
      ['', ''],
      ['', '> '],
    ],
  },
})
</script>

<template>
  <svg class="mac-terminal" viewBox="0 0 480 340" role="img" aria-label="A macOS Terminal window where a user starts an agent">
    <defs>
      <linearGradient id="mac-terminal-bar" x1="0" x2="0" y1="0" y2="1">
        <stop offset="0" stop-color="#4a4a4c" />
        <stop offset="1" stop-color="#363638" />
      </linearGradient>
      <filter id="mac-terminal-shadow" x="-15%" y="-15%" width="130%" height="140%">
        <feDropShadow dx="0" dy="10" stdDeviation="12" flood-color="#000" flood-opacity="0.35" />
      </filter>
    </defs>

    <rect width="480" height="340" rx="8" fill="#fff" />

    <g transform="translate(28 34)">
      <rect width="424" height="266" rx="10" fill="#1e1e1e" filter="url(#mac-terminal-shadow)" />
      <path d="M0 28 V10 a10 10 0 0 1 10 -10 H414 a10 10 0 0 1 10 10 V28 Z" fill="url(#mac-terminal-bar)" />
      <line x1="0" x2="424" y1="28.5" y2="28.5" stroke="#000" />

      <circle cx="16" cy="14" r="6" fill="#ff5f57" stroke="#e0443e" stroke-width="0.5" />
      <circle cx="36" cy="14" r="6" fill="#febc2e" stroke="#dea123" stroke-width="0.5" />
      <circle cx="56" cy="14" r="6" fill="#28c840" stroke="#1aab29" stroke-width="0.5" />
      <text x="212" y="18.5" text-anchor="middle" class="title">{{ title }}</text>

      <text v-for="([kind, line], i) in lines" :key="i" x="12" :y="54 + i * 21" xml:space="preserve" :class="['line', kind]">{{ line }}</text>
      <rect x="29" y="124" width="9" height="17" class="cursor" />
    </g>
  </svg>
</template>

<style scoped>
.mac-terminal {
  width: 100%;
}

.title {
  font-family: -apple-system, "SF Pro Text", var(--sans);
  font-size: 12.5px;
  font-weight: 500;
  fill: #c8c8ca;
}

.line {
  font-family: "SF Mono", Menlo, var(--mono);
  font-size: 14px;
  fill: #f2f2f2;
  white-space: pre;
}

.line.muted {
  fill: #a0a0a2;
}

.cursor {
  fill: #d0d0d0;
}
</style>
