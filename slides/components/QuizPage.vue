<!-- Inline SVG of a printed quiz page -->
<template>
  <svg class="fig" viewBox="0 0 480 448" role="img" aria-label="A printed quiz page with space for a handwritten answer">
    <rect width="480" height="448" rx="8" class="fig-bg" />
    <rect x="70" y="16" width="340" height="416" fill="#fff" stroke="#c9ccd1" />
    <text x="92" y="52" class="fig-head" style="font-size: 22px">Quiz 3</text>
    <text x="388" y="52" text-anchor="end" class="fig-note">Name: ____________</text>
    <text x="92" y="82" class="fig-note">No digital devices.</text>
    <text x="92" y="102" class="fig-note">One handwritten page of notes, front and back.</text>
    <text x="92" y="122" class="fig-note">Handwriting is 10% of the grade.</text>
    <line x1="92" x2="388" y1="138" y2="138" stroke="#c1a875" stroke-width="2" />
    <text x="92" y="168" class="fig-text" style="font-weight: 600">1. Parse Trees (10 points)</text>
    <text x="92" y="192" class="fig-text">Draw the parse tree for 1 + 2 * 3.</text>
    <text x="92" y="212" class="fig-text">Explain why * is lower in the tree.</text>
    <line v-for="i in 7" :key="i" x1="92" x2="388" :y1="210 + i * 28" :y2="210 + i * 28" stroke="#dfe1e5" />
  </svg>
</template>
