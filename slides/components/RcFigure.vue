<!-- Inline SVG of an interactive figure: the step response of an RC circuit -->
<script setup lang="ts">
const x0 = 60
const y0 = 280
const w = 360
const h = 180
const tau = w / 5
const points = Array.from({ length: 61 }, (_, i) => {
  const x = (i / 60) * w
  return `${(x0 + x).toFixed(1)},${(y0 - h * (1 - Math.exp(-x / tau))).toFixed(1)}`
}).join(' ')
const tauY = y0 - h * (1 - Math.exp(-1))
</script>

<template>
  <svg class="fig" viewBox="0 0 480 416" role="img" aria-label="An interactive plot of the step response of an RC circuit, with sliders for R and C">
    <rect width="480" height="416" rx="8" class="fig-bg" />
    <rect x="16" y="16" width="448" height="384" rx="7" class="fig-card" />
    <text x="36" y="50" class="fig-head">RC Step Response</text>

    <path :d="`M${x0} ${y0 - h - 10} V${y0} H${x0 + w + 10}`" fill="none" stroke="#5f6368" stroke-width="1.5" />
    <text x="36" :y="y0 - h" class="fig-mono">V</text>
    <text :x="x0 + w" :y="y0 + 20" class="fig-mono">t</text>
    <line :x1="x0" :x2="x0 + tau" :y1="tauY" :y2="tauY" stroke="#9aa0a6" stroke-dasharray="4 4" />
    <line :x1="x0 + tau" :x2="x0 + tau" :y1="tauY" :y2="y0" stroke="#9aa0a6" stroke-dasharray="4 4" />
    <polyline :points="points" fill="none" stroke="#00205b" stroke-width="3" />
    <circle :cx="x0 + tau" :cy="tauY" r="5" fill="#c1a875" />
    <text :x="x0 + tau + 12" :y="tauY + 22" class="fig-note">63% at one time constant</text>

    <g v-for="([label, knob], i) in [['R', 150], ['C', 230]]" :key="label" :transform="`translate(0 ${328 + i * 38})`">
      <text x="36" y="5" class="fig-mono">{{ label }}</text>
      <line x1="60" x2="430" stroke="#c9ccd1" stroke-width="4" stroke-linecap="round" />
      <circle :cx="knob" r="8" fill="#00205b" />
    </g>
  </svg>
</template>
