<!-- Inline SVG of my template folders and an excerpt of the slide rules -->
<script setup lang="ts">
const tree = [
  [0, 'dir', 'templates/', ''],
  [1, 'rule', 'AGENTS.md', 'all my courses'],
  [1, 'dir', 'agents/', ''],
  [2, 'file', 'LECTURES.md', 'slide rules'],
  [2, 'file', 'VOICE.md', 'how I write'],
  [2, 'file', 'QUIZZES.md', 'quiz rules'],
  [1, 'dir', 'csci-366-template/', ''],
  [2, 'rule', 'AGENTS.md', 'this course'],
]
const rules = [
  ['mark', '# Lectures'],
  ['', ''],
  ['', '* Usually use a two-cols layout'],
  ['', '* Three bullets per slide on the left'],
  ['', '* Use italics for emphasis'],
  ['', '* Avoid "filler" slides like "Pitfalls"'],
]
</script>

<template>
  <svg class="agents-file" viewBox="0 0 480 462" role="img" aria-label="Folders with AGENTS.md rule files, and an excerpt of the slide rules">
    <rect width="480" height="462" rx="8" class="backdrop" />

    <!-- folders -->
    <g transform="translate(16 16)">
      <rect width="448" height="218" rx="7" class="window" />
      <g v-for="([depth, kind, name, note], i) in tree" :key="i" :transform="`translate(0 ${28 + i * 24})`">
        <text :x="16 + depth * 22" :class="['name', kind]">{{ name }}</text>
        <text x="432" text-anchor="end" class="note">{{ note }}</text>
      </g>
    </g>

    <!-- rule file -->
    <g transform="translate(16 248)">
      <rect width="448" height="198" rx="7" class="window" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H441 a7 7 0 0 1 7 7 V28 Z" class="tab-strip" />
      <path d="M0 28 V7 a7 7 0 0 1 7 -7 H130 V28 Z" fill="#fff" />
      <text x="14" y="19" class="tab-title">LECTURES.md</text>
      <line x1="130" x2="448" y1="28.5" y2="28.5" stroke="#c9ccd1" />
      <text v-for="([kind, line], i) in rules" :key="i" x="16" :y="56 + i * 25" :class="['line', kind]">{{ line }}</text>
    </g>
  </svg>
</template>

<style scoped>
.agents-file {
  width: 100%;
}

.backdrop {
  fill: #f3f4f6;
}

.window {
  fill: #fff;
  stroke: #c9ccd1;
}

.name {
  font-family: var(--mono);
  font-size: 14px;
  fill: #3c4043;
}

.name.dir {
  fill: #7a808a;
}

.name.rule {
  fill: var(--msu-blue);
  font-weight: 600;
}

.note {
  font-family: var(--sans);
  font-style: italic;
  font-size: 14px;
  fill: #5f6368;
}

.tab-strip {
  fill: #e4e6ea;
}

.tab-title {
  font-family: var(--sans);
  font-size: 13px;
  fill: #3c4043;
}

.line {
  font-family: var(--mono);
  font-size: 13.5px;
  fill: #1c2534;
}

.line.mark {
  fill: var(--msu-blue);
  font-weight: 600;
}
</style>
