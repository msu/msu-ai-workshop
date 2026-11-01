<!-- Inline SVG of a markdown file above the slide it renders to -->
<script setup lang="ts">
const lines = [
  [['mark', '# '], ['head', 'Compilers']],
  [],
  [['mark', '* '], ['text', 'Turns '], ['em', '_source_'], ['text', ' into machine code']],
  [['mark', '* '], ['text', 'A parser builds a syntax tree']],
  [['mark', '* '], ['text', 'Example:']],
  [['code', '`1 + 2 * 3`']],
]
const edges = [[340, 74, 295, 124], [340, 74, 385, 124], [385, 124, 350, 174], [385, 124, 420, 174]]
const nodes = [[340, 74, '+'], [295, 124, '1'], [385, 124, '*'], [350, 174, '2'], [420, 174, '3']]
</script>

<template>
  <svg class="markdown-doc" viewBox="0 0 480 484" role="img" aria-label="A markdown file about compilers above the slide that it renders to">
    <rect width="480" height="484" rx="8" class="backdrop" />

    <!-- markdown file -->
    <g transform="translate(16 16)">
      <rect width="448" height="166" rx="7" class="editor" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V28 Z" class="tab-strip" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H176 V28 Z" fill="#fff" />
      <text x="14" y="19" class="tab-title">compilers.md</text>
      <line x1="176" x2="448" y1="28.5" y2="28.5" stroke="#c9ccd1" />
      <g v-for="(tokens, i) in lines" :key="i">
        <text x="26" :y="50 + i * 21" text-anchor="end" class="gutter">{{ i + 1 }}</text>
        <text x="40" :y="50 + i * 21" xml:space="preserve" class="line">
          <tspan v-for="([kind, value], j) in tokens" :key="j" :class="kind">{{ value }}</tspan>
        </text>
      </g>
    </g>

    <!-- arrow -->
    <path d="M240 188 V208 M233 201 L240 208 L247 201" class="arrow" />

    <!-- rendered slide -->
    <g transform="translate(16 216)">
      <rect width="448" height="252" rx="4" class="slide" />
      <text x="24" y="44" class="slide-title">Compilers</text>

      <circle cx="29" cy="80" r="2.5" class="dot" />
      <text x="40" y="85" class="slide-text">Turns <tspan class="slide-em">source</tspan> into machine code</text>
      <circle cx="29" cy="108" r="2.5" class="dot" />
      <text x="40" y="113" class="slide-text">A parser builds a syntax tree</text>
      <circle cx="29" cy="136" r="2.5" class="dot" />
      <text x="40" y="141" class="slide-text">Example:</text>
      <text x="40" y="172" class="slide-code">1 + 2 * 3</text>

      <!-- syntax tree -->
      <line v-for="([x1, y1, x2, y2], i) in edges" :key="i" :x1="x1" :y1="y1" :x2="x2" :y2="y2" class="edge" />
      <g v-for="([x, y, label], i) in nodes" :key="i">
        <circle :cx="x" :cy="y" r="15" class="node" />
        <text :x="x" :y="y + 5" text-anchor="middle" class="node-text">{{ label }}</text>
      </g>
    </g>
  </svg>
</template>

<style scoped>
.markdown-doc {
  width: 100%;
}

.backdrop {
  fill: #f3f4f6;
}

.editor {
  fill: #fff;
  stroke: #c9ccd1;
}

.tab-strip {
  fill: #e4e6ea;
}

.tab-title {
  font-family: var(--sans);
  font-size: 13px;
  fill: #3c4043;
}

.gutter {
  font-family: var(--mono);
  font-size: 11px;
  fill: #9aa0a6;
}

.line {
  font-family: var(--mono);
  font-size: 14px;
  fill: #1c2534;
  white-space: pre;
}

.mark {
  fill: #7a6636;
  font-weight: 600;
}

.head {
  fill: var(--msu-blue);
  font-weight: 600;
}

.em {
  font-style: italic;
}

.code {
  fill: #a0442c;
}

.arrow {
  fill: none;
  stroke: var(--msu-blue);
  stroke-width: 2;
}

.slide {
  fill: var(--paper);
}

.slide-title {
  font-family: var(--serif);
  font-size: 26px;
  font-weight: 600;
  fill: #fff;
}

.slide-text {
  font-family: var(--sans);
  font-size: 16px;
  fill: var(--ink);
}

.slide-code {
  font-family: var(--mono);
  font-size: 16px;
  fill: var(--msu-gold);
}

.slide-em {
  font-style: italic;
}

.dot {
  fill: var(--msu-gold);
}

.edge {
  stroke: var(--muted);
  stroke-width: 1.5;
}

.node {
  fill: var(--panel);
  stroke: var(--msu-gold);
  stroke-width: 1.5;
}

.node-text {
  font-family: var(--mono);
  font-size: 15px;
  fill: #fff;
}
</style>
