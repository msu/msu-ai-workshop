<!-- Inline SVG of the context menu that my IntelliJ plugin adds -->
<script setup lang="ts">
const items = [
  ['plain', 'Cut'],
  ['plain', 'Copy'],
  ['plain', 'Paste'],
  ['rule', ''],
  ['active', 'Launch in Slidev'],
  ['plain', 'Export to PDF (Pandoc)'],
  ['plain', 'Print (Pandoc)'],
]
const lines = ['# Compilers', '* Turns _source_ into machine code', '* A parser builds a syntax tree']
</script>

<template>
  <svg class="fig" viewBox="0 0 480 372" role="img" aria-label="A context menu in IntelliJ with Launch in Slidev, Export to PDF and Print">
    <rect width="480" height="372" rx="8" class="fig-bg" />
    <g transform="translate(16 16)">
      <rect width="448" height="340" rx="7" fill="#1e1f22" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V28 Z" fill="#2b2d30" />
      <text x="14" y="19" class="fig-tab" style="fill: #dfe1e5">compilers.md</text>
      <text v-for="(line, i) in lines" :key="i" x="16" :y="56 + i * 24" class="fig-mono" style="fill: #bcbec4">{{ line }}</text>
    </g>
    <g transform="translate(150 140)">
      <rect width="280" height="212" rx="7" fill="#2b2d30" stroke="#4e5157" />
      <template v-for="(item, i) in items" :key="i">
        <line v-if="item[0] === 'rule'" x1="8" x2="272" :y1="10 + i * 28 + 14" :y2="10 + i * 28 + 14" stroke="#4e5157" />
        <template v-else>
          <rect v-if="item[0] === 'active'" x="6" :y="8 + i * 28" width="268" height="27" rx="4" fill="#00205b" />
          <text x="18" :y="27 + i * 28" class="fig-text" style="fill: #fff">{{ item[1] }}</text>
        </template>
      </template>
    </g>
  </svg>
</template>
