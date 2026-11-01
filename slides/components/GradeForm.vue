<!-- Inline SVG of the university grade form, filled in by the generated JavaScript.
     The names are fake. The console lines follow generate_grade_script.py -->
<script setup lang="ts">
const students = [
  ['Bobcat, Bailey', '94.2', 'A'],
  ['Champ, Casey', '88.1', 'B+'],
  ['Gallatin, Gray', '90.3', 'A-'],
  ['Madison, Morgan', '71.4', 'C-'],
  ['Yellowstone, Yael', '83.0', 'B'],
]
const consoleLines = [
  ['in', '> const grades = [ /* from the CSV */ ];'],
  ['code', '  grades.forEach(g => {'],
  ['code', '    const row = findRow(g.name);'],
  ['code', '    row.select.value = g.grade;'],
  ['code', '  });'],
  ['ok', 'All students matched successfully'],
]
</script>

<template>
  <svg class="fig" viewBox="0 0 480 448" role="img" aria-label="A grade form in a browser. A script pasted in the console fills in the grade for each student">
    <rect width="480" height="448" rx="8" class="fig-bg" />

    <g transform="translate(16 16)">
      <rect width="448" height="416" rx="7" fill="#fff" stroke="#c9ccd1" />
      <path d="M0 30 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V30 Z" fill="#dee1e6" />
      <circle cx="13" cy="15" r="4" fill="#ff5f57" />
      <circle cx="26" cy="15" r="4" fill="#febc2e" />
      <circle cx="39" cy="15" r="4" fill="#28c840" />
      <path d="M54 30 V12 a6 6 0 0 1 6 -6 H180 a6 6 0 0 1 6 6 V30 Z" fill="#fff" />
      <text x="64" y="22" class="fig-tab">Final Grade Entry</text>

      <text x="16" y="52" class="fig-note" style="font-style: normal; font-weight: 600">Student</text>
      <text x="218" y="52" class="fig-note" style="font-style: normal; font-weight: 600">Score</text>
      <text x="306" y="52" class="fig-note" style="font-style: normal; font-weight: 600">Final Grade</text>

      <g v-for="([name, score, grade], i) in students" :key="name" :transform="`translate(0 ${60 + i * 34})`">
        <line x1="0.5" x2="447.5" y1="0" y2="0" stroke="#e4e6ea" />
        <text x="16" y="23" class="fig-text" style="fill: #003a8c">{{ name }}</text>
        <text x="218" y="23" class="fig-mono">{{ score }}</text>
        <rect x="306" y="6" width="120" height="23" rx="3" fill="#fff" stroke="#9aa0a6" />
        <path d="M410 15 l4 5 l4 -5" fill="none" stroke="#5f6368" stroke-width="1.5" />
        <text x="316" y="23" class="fig-text picked" :style="`animation-delay: ${i * 0.45}s`">{{ grade }}</text>
      </g>

      <!-- developer console -->
      <path d="M0 238 H448 V409 a7 7 0 0 1 -7 7 H7 a7 7 0 0 1 -7 -7 Z" fill="#1c1c1e" />
      <text x="14" y="258" class="console-tab">Console</text>
      <line x1="14" x2="62" y1="265" y2="265" stroke="#6f8fe0" stroke-width="2" />
      <text v-for="([kind, line], i) in consoleLines" :key="i" x="14" :y="288 + i * 21" xml:space="preserve" :class="['console', kind]">{{ line }}</text>
    </g>
  </svg>
</template>

<style scoped>
.picked {
  font-weight: 600;
  animation: pick 7s infinite both;
}

@keyframes pick {
  0% { opacity: 0; }
  6%, 92% { opacity: 1; }
  100% { opacity: 0; }
}

.console-tab {
  font-family: var(--sans);
  font-size: 12.5px;
  fill: #e6e9ef;
}

.console {
  font-family: var(--mono);
  font-size: 13.5px;
  fill: #c7c7cc;
  white-space: pre;
}

.console.in {
  fill: #fff;
}

.console.ok {
  fill: #56d364;
}
</style>
