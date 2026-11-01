<!-- Inline SVG: guards keep student data from company LLMs. CatChat is the careful exception -->
<script setup lang="ts">
const bricks: { x: number, y: number, w: number }[] = []
for (let row = 0; row < 3; row++) {
  const offset = row % 2 === 0 ? 0 : -19
  for (let i = 0; i < 9; i++) {
    const x = Math.max(16, 16 + offset + i * 38)
    const end = Math.min(16 + offset + i * 38 + 36, 268)
    if (end > x) bricks.push({ x, y: 196 + row * 15, w: end - x })
  }
}
</script>

<template>
  <svg class="fig" viewBox="0 0 480 432" role="img" aria-label="Guards block student data from company LLMs. A careful path goes through to the MSU CatChat models">
    <rect width="480" height="432" rx="8" class="fig-bg" />

    <!-- company LLMs -->
    <rect x="16" y="16" width="216" height="96" rx="6" class="fig-card" />
    <text x="124" y="48" text-anchor="middle" class="fig-head">ChatGPT, Claude</text>
    <text x="124" y="72" text-anchor="middle" class="fig-note">private companies</text>
    <text x="124" y="92" text-anchor="middle" class="fig-note">assume it is not private</text>

    <!-- CatChat -->
    <rect x="248" y="16" width="216" height="96" rx="6" class="fig-card" />
    <text x="356" y="48" text-anchor="middle" class="fig-head">CatChat</text>
    <text x="356" y="72" text-anchor="middle" class="fig-note">MSU models</text>
    <text x="356" y="92" text-anchor="middle" class="fig-note">through catatui</text>

    <!-- guards, with a gap for CatChat -->
    <rect v-for="(b, i) in bricks" :key="i" :x="b.x" :y="b.y" :width="b.w" height="13" rx="1.5" fill="#a0442c" />
    <rect x="296" y="196" width="168" height="43" rx="3" fill="none" stroke="#a0442c" stroke-dasharray="5 4" />
    <text x="368" y="222" class="fig-note" style="fill: #7a6636; font-weight: 600">be careful</text>
    <text x="16" y="186" class="fig-stop-text" style="fill: #a0442c">my guards</text>

    <!-- blocked path -->
    <path d="M112 156 L136 180 M136 156 L112 180" class="fig-stop" style="stroke-width: 3.5" />
    <path d="M124 330 V246" class="fig-stop" stroke-dasharray="6 5" />

    <!-- careful path -->
    <path d="M356 330 V116 M348 125 L356 116 L364 125" fill="none" stroke="#c1a875" stroke-width="3" />

    <!-- student data -->
    <rect x="16" y="330" width="448" height="86" rx="6" fill="#00205b" />
    <text x="240" y="366" text-anchor="middle" class="fig-head" style="fill: #fff; font-size: 21px">Student Data</text>
    <text x="240" y="393" text-anchor="middle" class="fig-text" style="fill: #dfe5f0">FERPA protected</text>
  </svg>
</template>
