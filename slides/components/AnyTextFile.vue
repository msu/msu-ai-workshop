<!-- Inline SVG, not an image file, so the text can use the deck fonts -->
<script setup lang="ts">
const session = [
  ['prompt', '> what does this project do?'],
  ['tool', '  Read AGENTS.md'],
  ['tool', '  Read lectures/ (38 files)'],
  ['tool', '  Bash git log --oneline -5'],
  ['reply', '  A systems course built around'],
  ['reply', '  two teaching CPUs...'],
]
const files = [
  ['Lecture', 'lecture_05.md'],
  ['Quiz', 'quiz_3.md'],
  ['Syllabus', 'syllabus.md'],
  ['Grading', 'grades.py'],
  ['Lab Report', 'lab_report.tex'],
  ['MATLAB', 'beam_model.m'],
]
</script>

<template>
  <svg class="any-text-file" viewBox="0 0 480 448" role="img" aria-label="A coding agent can work on lectures, quizzes, syllabi, grading scripts, lab reports and MATLAB files">
    <rect width="480" height="448" rx="8" class="backdrop" />
    <text x="16" y="32" class="heading">One Agent, Any Text File</text>

    <!-- terminal -->
    <g transform="translate(16 46)">
      <rect width="448" height="188" rx="7" class="terminal" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V28 Z" class="title-bar" />
      <circle cx="13" cy="14" r="4" fill="#ff5f57" />
      <circle cx="26" cy="14" r="4" fill="#febc2e" />
      <circle cx="39" cy="14" r="4" fill="#28c840" />
      <text x="224" y="18.5" text-anchor="middle" class="title-text">my-course -- claude</text>
      <text v-for="([kind, line], i) in session" :key="line" x="14" :y="52 + i * 24" xml:space="preserve" :class="['term', kind]">{{ line }}</text>
    </g>

    <!-- files -->
    <g v-for="([kind, name], i) in files" :key="name" :transform="`translate(${16 + (i % 3) * 153} ${246 + Math.floor(i / 3) * 98})`">
      <rect width="142" height="88" rx="6" class="tile" />
      <path d="M12 12 H24 L32 20 V40 H12 Z M24 12 V20 H32" class="icon" />
      <text x="42" y="32" class="tile-heading">{{ kind }}</text>
      <text x="12" y="68" class="tile-code">{{ name }}</text>
    </g>
  </svg>
</template>

<style scoped>
.any-text-file {
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

.term.prompt,
.term.reply {
  fill: #fff;
}

.tile {
  fill: #fff;
  stroke: #c9ccd1;
}

.icon {
  fill: none;
  stroke: var(--msu-blue);
  stroke-width: 1.6;
  stroke-linejoin: round;
}

.tile-heading {
  font-family: var(--serif);
  font-size: 16px;
  font-weight: 600;
  fill: var(--msu-blue);
}

.tile-code {
  font-family: var(--mono);
  font-size: 12.5px;
  fill: #3c4043;
}
</style>
