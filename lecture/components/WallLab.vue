<script setup>
import { ref, computed } from 'vue'

// Water depth in m. Wall height equals water depth. Values are per m of wall.
const h = ref(1.5)
const G = 9.81                                  // rho * g for water, kN/m^3

const w0 = computed(() => G * h.value)          // kN/m at the base
const vBase = computed(() => G * h.value ** 2 / 2)   // kN
const mBase = computed(() => G * h.value ** 3 / 6)   // kN*m

// Wall drawing: base at y=340, 5 m = 280 px
const base = 340
const px = 56
const wallX = 200
const top = computed(() => base - h.value * px)
const triLen = computed(() => w0.value * 2.4)

// M_base vs h chart, h in 0..5, M in 0..210
const CX0 = 330
const CX1 = 570
const CY0 = 340
const CY1 = 60
const cx = hh => CX0 + (hh / 5) * (CX1 - CX0)
const cy = m => CY0 - (m / 210) * (CY0 - CY1)
const curve = Array.from({ length: 51 }, (_, i) => {
  const hh = i / 10
  return `${cx(hh).toFixed(1)},${cy(G * hh ** 3 / 6).toFixed(1)}`
}).join(' ')
</script>

<template>
  <div class="lab">
    <svg viewBox="0 0 600 380" font-family="Atkinson Hyperlegible, Helvetica, Arial, sans-serif">
      <rect x="0" y="0" width="600" height="380" rx="14" fill="#f8fafc" />
      <rect x="20" :y="base" width="280" height="24" fill="#d6d3d1" />
      <rect x="40" :y="top" :width="wallX - 40" :height="base - top" fill="#38bdf8" fill-opacity="0.35" />
      <rect :x="wallX" :y="top - 10" width="22" :height="base - top + 10" fill="#475569" />
      <polygon :points="`${wallX},${top} ${wallX - triLen},${base} ${wallX},${base}`"
               fill="#dc2626" fill-opacity="0.15" stroke="#dc2626" stroke-width="2" />
      <text :x="wallX + 32" :y="(top + base) / 2" style="font-size: 18px" font-style="italic" fill="#1e293b">h</text>

      <line :x1="CX0" :y1="CY0" :x2="CX1" :y2="CY0" stroke="#94a3b8" stroke-width="1.5" />
      <line :x1="CX0" :y1="CY0" :x2="CX0" :y2="CY1" stroke="#94a3b8" stroke-width="1.5" />
      <polyline :points="curve" fill="none" stroke="#c026d3" stroke-width="3" />
      <circle :cx="cx(h)" :cy="cy(mBase)" r="7" fill="#c026d3" />
      <text :x="CX1" :y="CY0 + 22" style="font-size: 14px" text-anchor="end" fill="#475569">h (m)</text>
      <text :x="CX0 + 8" :y="CY1 - 8" style="font-size: 14px" fill="#475569">M_base</text>
    </svg>
    <input type="range" min="0.5" max="5" step="0.1" v-model.number="h" />
    <div class="readout">
      <span>h = {{ h.toFixed(1) }} m</span>
      <span>V = {{ vBase.toFixed(1) }} kN</span>
      <span>M = {{ mBase.toFixed(1) }} kN*m</span>
    </div>
  </div>
</template>

<style scoped>
.lab { display: flex; flex-direction: column; gap: 0.4rem; }
input { width: 100%; }
.readout { display: flex; justify-content: space-between; font-family: var(--slidev-code-font-family, monospace); font-size: 0.85rem; }
</style>
