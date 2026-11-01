<!-- Inline SVG of a diff of a quiz file -->
<script setup lang="ts">
const lines = [
  ['same', '1', '1', '  # Quiz 3'],
  ['same', '2', '2', ''],
  ['same', '3', '3', '  1. What does a compiler do?'],
  ['del', '4', '', '- 2. Explain a parse tree.'],
  ['add', '', '4', '+ 2. Draw the parse tree for 1 + 2 * 3.'],
  ['add', '', '5', '+    Show your work.'],
  ['same', '5', '6', '  3. What is a linker?'],
]
</script>

<template>
  <svg class="text-diff" viewBox="0 0 480 292" role="img" aria-label="A diff of a quiz file: one line removed in red and two lines added in green">
    <rect width="480" height="292" rx="8" class="backdrop" />

    <g transform="translate(16 16)">
      <rect width="448" height="260" rx="7" class="window" />
      <path d="M0 34 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V34 Z" class="header" />
      <text x="14" y="22" class="file">quiz_3.md</text>
      <text x="400" y="22" text-anchor="end" class="count-add">+2</text>
      <text x="434" y="22" text-anchor="end" class="count-del">-1</text>

      <g v-for="([kind, oldNo, newNo, text], i) in lines" :key="i" :transform="`translate(0 ${34 + i * 32})`">
        <rect v-if="kind !== 'same'" x="0.5" width="447" height="32" :class="`bg-${kind}`" />
        <text x="24" y="21" text-anchor="end" class="gutter">{{ oldNo }}</text>
        <text x="48" y="21" text-anchor="end" class="gutter">{{ newNo }}</text>
        <text x="58" y="21" xml:space="preserve" :class="['code', kind]">{{ text }}</text>
      </g>
    </g>
  </svg>
</template>

<style scoped>
.text-diff {
  width: 100%;
}

.backdrop {
  fill: #f3f4f6;
}

.window {
  fill: #fff;
  stroke: #c9ccd1;
}

.header {
  fill: #e4e6ea;
}

.file {
  font-family: var(--mono);
  font-size: 13px;
  fill: #1c2534;
}

.count-add,
.count-del {
  font-family: var(--mono);
  font-size: 13px;
  font-weight: 600;
}

.count-add {
  fill: #1a7f37;
}

.count-del {
  fill: #cf222e;
}

.bg-del {
  fill: #ffebe9;
}

.bg-add {
  fill: #dafbe1;
}

.gutter {
  font-family: var(--mono);
  font-size: 11px;
  fill: #8c959f;
}

.code {
  font-family: var(--mono);
  font-size: 14px;
  fill: #1c2534;
  white-space: pre;
}

.code.del {
  fill: #a40e26;
}

.code.add {
  fill: #116329;
}

</style>
