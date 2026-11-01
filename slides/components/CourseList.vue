<!-- Inline SVG, not an image file, so the text can use the deck fonts -->
<script setup lang="ts">
const courses = [
  ['CSCI 366', 'Computer Systems'],
  ['CSCI 431', 'Hypermedia Systems'],
  ['CSCI 440', 'Database Systems'],
  ['CSCI 468', 'Compilers'],
  ['ESOF 322', 'Software Engineering'],
]
</script>

<template>
  <svg class="course-list" viewBox="0 0 420 318" role="img" aria-label="Courses I teach">
    <text x="210" y="24" text-anchor="middle" class="title">Courses I Teach</text>
    <g v-for="([code, name], i) in courses" :key="code" :transform="`translate(0 ${48 + i * 54})`">
      <line x1="0" x2="420" y1="0" y2="0" class="rule" />
      <text x="0" y="34" class="code">{{ code }}</text>
      <text x="112" y="35" class="name">{{ name }}</text>
    </g>
  </svg>
</template>

<style scoped>
.course-list {
  width: 100%;
}

.rule {
  stroke: var(--line);
}

.title {
  font-family: var(--sans);
  font-size: 22px;
  font-weight: 600;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  fill: var(--msu-gold);
}

.code {
  font-family: var(--mono);
  font-size: 15px;
  fill: var(--msu-gold);
}

.name {
  font-family: var(--serif);
  font-size: 22px;
  fill: var(--ink);
}
</style>
