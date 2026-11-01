<!-- Inline SVG of a prompt and the printed pages it makes.
     The rubric and note sections come from agents/QUIZZES.md and agents/SPEAKER-NOTES.md.
     The quiz question is an example, not from a real quiz -->
<script setup lang="ts">
const key = [
  ['head', 'Question 1'],
  ['text', 'Flip the bits, add 1.'],
  ['gap', ''],
  ['head', 'Grading'],
  ['text', '10  perfect'],
  ['text', '8-9  close'],
  ['text', '7  serious problems'],
  ['text', '5  reasonable effort'],
  ['text', '3  anything at all'],
]
const notes = ['Announcements', 'Lecture Summary', 'Demos', 'Lecture Observations']
</script>

<template>
  <svg class="fig" viewBox="0 0 480 416" role="img" aria-label="A prompt to an agent makes a printed quiz, an answer key with a grading scale, and podium notes">
    <rect width="480" height="416" rx="8" class="fig-bg" />

    <!-- prompt -->
    <rect x="16" y="16" width="448" height="62" rx="7" fill="#1c1c1e" />
    <text x="30" y="42" class="prompt">&gt; propose quiz questions from lectures 4 to 6</text>
    <text x="30" y="63" class="prompt muted">  I like 2, 3 and 5. make the quiz and the key</text>

    <!-- quiz -->
    <g transform="translate(16 92) rotate(-1.2 70 150)">
      <rect width="142" height="306" class="page" />
      <text x="11" y="26" class="page-title">Quiz 3</text>
      <text x="11" y="46" class="small">No digital devices</text>
      <text x="11" y="62" class="small">One page of notes</text>
      <line x1="11" x2="131" y1="72" y2="72" stroke="#c1a875" stroke-width="1.5" />
      <text x="11" y="92" class="small strong">1. Two's Complement</text>
      <text x="11" y="110" class="small">Negate 00010110,</text>
      <text x="11" y="126" class="small">and show your work.</text>
      <line v-for="i in 8" :key="i" x1="11" x2="131" :y1="130 + i * 20" :y2="130 + i * 20" stroke="#e4e6ea" />
    </g>

    <!-- answer key -->
    <g transform="translate(169 92)">
      <rect width="142" height="306" class="page" />
      <text x="11" y="26" class="page-title">Answer Key</text>
      <text x="11" y="46" class="small">For the TA</text>
      <line x1="11" x2="131" y1="56" y2="56" stroke="#c1a875" stroke-width="1.5" />
      <text v-for="([kind, line], i) in key" :key="i" x="11" :y="78 + i * 21" :class="['small', kind === 'head' && 'strong']">{{ line }}</text>
    </g>

    <!-- podium notes -->
    <g transform="translate(322 92) rotate(1.2 70 150)">
      <rect width="142" height="306" class="page" />
      <text x="11" y="26" class="page-title">Podium Notes</text>
      <text x="11" y="46" class="small">Lecture 6</text>
      <g v-for="(name, i) in notes" :key="name" :transform="`translate(0 ${56 + i * 60})`">
        <line x1="11" x2="131" y1="0" y2="0" stroke="#c1a875" stroke-width="1.5" />
        <text x="11" y="20" class="small strong">{{ name }}</text>
        <line v-if="i < 3" x1="11" x2="110" y1="33" y2="33" stroke="#c9ccd1" stroke-width="2" />
        <line v-if="i < 3" x1="11" x2="90" y1="44" y2="44" stroke="#c9ccd1" stroke-width="2" />
      </g>
    </g>
  </svg>
</template>

<style scoped>
.prompt {
  font-family: var(--mono);
  font-size: 13.5px;
  fill: #fff;
  white-space: pre;
}

.prompt.muted {
  fill: #c7c7cc;
}

.page {
  fill: #fff;
  stroke: #c9ccd1;
}

.page-title {
  font-family: var(--serif);
  font-size: 17px;
  font-weight: 600;
  fill: var(--msu-blue);
}

.small {
  font-family: var(--sans);
  font-size: 13px;
  fill: #1c2534;
}

.strong {
  font-weight: 600;
}
</style>
