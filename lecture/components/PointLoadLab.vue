<script setup>
import { ref, computed } from 'vue'

// a/L, the load position as a fraction of the span
const t = ref(0.33)

const X0 = 60
const X1 = 540
const X = f => X0 + f * (X1 - X0)

const ra = computed(() => 1 - t.value)          // R_A / P
const rb = computed(() => t.value)              // R_B / P
const mmax = computed(() => t.value * (1 - t.value))  // M_max / PL

// V panel: zero line at 200, 1 P = 60 px
const vz = 200
const vs = 60
const vPath = computed(() => {
  const a = X(t.value)
  return `${X0},${vz} ${X0},${vz - ra.value * vs} ${a},${vz - ra.value * vs} ` +
         `${a},${vz + rb.value * vs} ${X1},${vz + rb.value * vs} ${X1},${vz}`
})

// M panel: zero line at 380, 0.25 PL = 100 px
const mz = 380
const ms = 400
const mPath = computed(() => `${X0},${mz} ${X(t.value)},${mz - mmax.value * ms} ${X1},${mz}`)
</script>

<template>
  <div class="lab">
    <svg viewBox="0 0 600 400" font-family="Atkinson Hyperlegible, Helvetica, Arial, sans-serif">
      <defs>
        <marker id="pl-ah" viewBox="0 0 10 10" refX="8" refY="5" markerWidth="5" markerHeight="5" orient="auto">
          <path d="M0,0 L10,5 L0,10 z" fill="#dc2626" />
        </marker>
      </defs>
      <rect x="0" y="0" width="600" height="400" rx="14" fill="#f8fafc" />
      <rect :x="X0" y="73" :width="X1 - X0" height="14" rx="2" fill="#475569" />
      <path :d="`M ${X0} 87 l -12 18 l 24 0 z`" fill="none" stroke="#1e293b" stroke-width="2" />
      <path :d="`M ${X1} 87 l -12 14 l 24 0 z`" fill="none" stroke="#1e293b" stroke-width="2" />
      <circle :cx="X1 - 6" cy="105" r="3.5" fill="none" stroke="#1e293b" stroke-width="2" />
      <circle :cx="X1 + 6" cy="105" r="3.5" fill="none" stroke="#1e293b" stroke-width="2" />
      <line :x1="X(t)" y1="20" :x2="X(t)" y2="68" stroke="#dc2626" stroke-width="3" marker-end="url(#pl-ah)" />
      <text :x="X(t) + 10" y="30" fill="#dc2626" style="font-size: 16px">P</text>

      <line :x1="X0" :y1="vz" :x2="X1" :y2="vz" stroke="#94a3b8" stroke-width="1.5" />
      <polygon :points="vPath" fill="#0891b2" fill-opacity="0.15" stroke="#0891b2" stroke-width="3" />
      <text x="30" :y="vz + 6" fill="#0891b2" style="font-size: 20px" font-weight="bold" font-style="italic">V</text>

      <line :x1="X0" :y1="mz" :x2="X1" :y2="mz" stroke="#94a3b8" stroke-width="1.5" />
      <polygon :points="mPath" fill="#c026d3" fill-opacity="0.15" stroke="#c026d3" stroke-width="3" />
      <text x="30" :y="mz - 20" fill="#c026d3" style="font-size: 20px" font-weight="bold" font-style="italic">M</text>
      <line :x1="X(0.5)" :y1="mz - 108" :x2="X(0.5)" :y2="mz" stroke="#94a3b8" stroke-dasharray="3 4" />
    </svg>
    <input type="range" min="0.02" max="0.98" step="0.01" v-model.number="t" />
    <div class="readout">
      <span>a/L = {{ t.toFixed(2) }}</span>
      <span>R_A = {{ ra.toFixed(2) }} P</span>
      <span>M_max = {{ mmax.toFixed(3) }} PL</span>
    </div>
  </div>
</template>

<style scoped>
.lab { display: flex; flex-direction: column; gap: 0.4rem; }
input { width: 100%; }
.readout { display: flex; justify-content: space-between; font-family: var(--slidev-code-font-family, monospace); font-size: 0.85rem; }
</style>
