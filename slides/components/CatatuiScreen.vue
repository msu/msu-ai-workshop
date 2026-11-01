<!-- Inline SVG of the catatui startup screen in the dark theme.
     The art and palette come from catatui/src/ts/logo.ts. Every pixel is solid here,
     so the bobcat reads at slide size -->
<script setup lang="ts">
const ART = [
  '..................C......',
  '.................CNC.....',
  '...............CCNNN.....',
  '..............CCNNNN.....',
  '.............CNNNGNC.....',
  '...........CCNNGGGN......',
  '.........CCNNNGNGGNCC....',
  '.......CCNNNNNNNGGGNNC...',
  '.....CCNNNGGGNGNGGGGNN...',
  '....CCNNGGGGGGGGGGNGGNN..',
  '...CCNNGGGGGGNGGGGGNNGNC.',
  '..CNNNGGGGGGNGGGGGGGGNGNC',
  '.CNNGGGGNGGNNNGGGGGGGGCGN',
  'CNNNGGGNGGGGNGGGGCCCNNCCC',
  'CNNNNNNNGGGNNGGGGCCNCNNN.',
  'CNCCNNNNNNNNNGGCCCCNCCC..',
  '.C..CNNNNNNNNGNNNCCNNN...',
  '.....CGGGCNNNNNCCNCCCN...',
  '..........CNNNC.CNNNNC...',
  '...........CNNC...CNC....',
  '...........GNNC....C.....',
  '............GN...........',
  '.............G...........',
  '.........................',
]
const palette: Record<string, string> = { N: 'rgb(0,143,17)', G: 'rgb(0,255,65)', C: 'rgb(170,255,190)' }

const cells: { x: number, y: number, fill: string }[] = []
for (let y = 0; y < ART.length; y++) {
  for (let x = 0; x < ART[0].length; x++) {
    const fill = palette[ART[y][x]]
    if (fill) cells.push({ x: x * 6, y: y * 6, fill })
  }
}

const commands = [
  ['/login catchat', 'sign in'],
  ['/model', 'pick a model'],
  ['/catchat', 'status'],
  ['/hotkeys', 'keys'],
]
</script>

<template>
  <svg class="fig" viewBox="0 0 480 300" role="img" aria-label="The catatui startup screen in a dark terminal, with a green pixel-art bobcat">
    <rect width="480" height="300" rx="10" fill="#1e1e1e" />
    <path d="M0 28 V10 a10 10 0 0 1 10 -10 H470 a10 10 0 0 1 10 10 V28 Z" fill="#3a3a3c" />
    <circle cx="16" cy="14" r="6" fill="#ff5f57" />
    <circle cx="36" cy="14" r="6" fill="#febc2e" />
    <circle cx="56" cy="14" r="6" fill="#28c840" />
    <text x="240" y="18.5" text-anchor="middle" class="bar-title">my-course -- catatui</text>

    <g transform="translate(16 44)">
      <rect v-for="(c, i) in cells" :key="i" :x="c.x" :y="c.y" width="6" height="6" :fill="c.fill" />
    </g>

    <text x="184" y="84" class="term" style="fill: #f4b425; font-weight: 600">catatui <tspan class="plain" style="fill: #666666">v0.5.2</tspan></text>
    <text x="184" y="102" class="term" style="fill: #808080">Montana State Command Line Agent</text>
    <g v-for="([cmd, what], i) in commands" :key="cmd">
      <text x="184" :y="132 + i * 18" class="term" style="fill: #666666">{{ cmd }}</text>
      <text x="306" :y="132 + i * 18" class="term" style="fill: #808080">{{ what }}</text>
    </g>

    <line x1="12" x2="468" y1="214" y2="214" stroke="#6f8fe0" />
    <rect x="16" y="222" width="8" height="16" fill="#d4d4d4" />
    <line x1="12" x2="468" y1="246" y2="246" stroke="#6f8fe0" />

    <text x="12" y="272" class="foot">
      <tspan style="fill: #666666">cwd:</tspan> <tspan style="fill: #808080">~/my-course (main)</tspan>
      <tspan style="fill: #666666" dx="6">model:</tspan> <tspan style="fill: #808080">gpt-oss:120b</tspan>
      <tspan style="fill: #666666" dx="6">ctx:</tspan> <tspan style="fill: #808080">0.0% of 115k</tspan>
    </text>
    <text x="12" y="289" class="foot"><tspan style="fill: #666666">mode:</tspan> <tspan style="fill: #808080">ask</tspan></text>
  </svg>
</template>

<style scoped>
.bar-title {
  font-family: -apple-system, "SF Pro Text", var(--sans);
  font-size: 12.5px;
  font-weight: 500;
  fill: #c8c8ca;
}

.term {
  font-family: "SF Mono", Menlo, var(--mono);
  font-size: 12.5px;
}

.plain {
  font-weight: 400;
}

.foot {
  font-family: "SF Mono", Menlo, var(--mono);
  font-size: 10.5px;
}
</style>
