<!-- Inline SVG, not an image file, so the text can use the deck fonts -->
<script setup lang="ts">
const session = [
  ['prompt', '> fix the typo on slide 4'],
  ['tool', '  Read 20_compilers.md'],
  ['tool', '  Edit 20_compilers.md'],
  ['del', '  - a compilier turns source'],
  ['add', '  + a compiler turns source'],
  ['prompt', '> good, now build the PDF'],
  ['tool', '  Run  npm run export'],
]
</script>

<template>
  <svg class="coding-agent" viewBox="0 0 480 448" role="img" aria-label="A coding agent runs on your computer, where it reads and writes files and runs commands">
    <rect width="480" height="448" rx="8" class="backdrop" />
    <text x="16" y="32" class="heading">Your Computer</text>

    <!-- terminal -->
    <g transform="translate(16 46)">
      <rect width="448" height="226" rx="7" class="terminal" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V28 Z" class="title-bar" />
      <circle cx="13" cy="14" r="4" fill="#ff5f57" />
      <circle cx="26" cy="14" r="4" fill="#febc2e" />
      <circle cx="39" cy="14" r="4" fill="#28c840" />
      <text x="224" y="18.5" text-anchor="middle" class="title-text">my-course -- claude</text>
      <text v-for="([kind, line], i) in session" :key="line" x="14" :y="54 + i * 25" xml:space="preserve" :class="['term', kind]">{{ line }}</text>
    </g>

    <!-- arrows -->
    <path d="M124 278 V312 M118 285 L124 278 L130 285 M118 305 L124 312 L130 305" class="arrow" />
    <path d="M356 278 V312 M350 305 L356 312 L362 305" class="arrow" />

    <!-- files -->
    <g transform="translate(16 318)">
      <rect width="216" height="114" rx="6" class="tile" />
      <path d="M18 18 H42 L54 30 V62 H18 Z M42 18 V30 H54" class="icon" />
      <text x="68" y="36" class="tile-heading">Files</text>
      <text x="68" y="56" class="tile-point">read and write</text>
      <text x="18" y="94" class="tile-code">20_compilers.md</text>
    </g>

    <!-- commands -->
    <g transform="translate(248 318)">
      <rect width="216" height="114" rx="6" class="tile" />
      <rect x="18" y="20" width="38" height="40" rx="4" class="prompt-icon" />
      <path d="M25 32 l7 7 l-7 7 M36 48 h12" class="prompt-mark" />
      <text x="70" y="36" class="tile-heading">Commands</text>
      <text x="70" y="56" class="tile-point">run them locally</text>
      <text x="18" y="94" class="tile-code">npm run export</text>
    </g>
  </svg>
</template>

<style scoped>
.coding-agent {
  width: 100%;
}

.backdrop {
  fill: #f3f4f6;
}

.heading {
  font-family: var(--serif);
  font-size: 19px;
  font-weight: 600;
  fill: var(--msu-blue);
}

.terminal {
  fill: #1c1c1e;
}

.title-bar {
  fill: #3a3a3c;
}

.title-text {
  font-family: var(--sans);
  font-size: 12px;
  fill: #d1d1d6;
}

.term {
  font-family: var(--mono);
  font-size: 14px;
  fill: #c7c7cc;
  white-space: pre;
}

.term.prompt {
  fill: #fff;
}

.term.del {
  fill: #ff7b72;
}

.term.add {
  fill: #56d364;
}

.arrow {
  fill: none;
  stroke: var(--msu-blue);
  stroke-width: 2;
}

.tile {
  fill: #fff;
  stroke: #c9ccd1;
}

.icon {
  fill: none;
  stroke: var(--msu-blue);
  stroke-width: 2;
  stroke-linejoin: round;
}

.prompt-icon {
  fill: #1c1c1e;
}

.prompt-mark {
  fill: none;
  stroke: #fff;
  stroke-width: 2;
}

.tile-heading {
  font-family: var(--serif);
  font-size: 18px;
  font-weight: 600;
  fill: var(--msu-blue);
}

.tile-point {
  font-family: var(--sans);
  font-size: 15px;
  fill: #1c2534;
}

.tile-code {
  font-family: var(--mono);
  font-size: 13.5px;
  fill: #3c4043;
}
</style>
