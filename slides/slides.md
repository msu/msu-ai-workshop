---
title: Effective AI For Engineering Faculty
info: Montana State University faculty workshop, Nov 4 2026, NAH 137
colorSchema: dark
defaults:
  layout: two-cols
mdc: true
fonts:
  sans: Source Sans 3
  serif: Source Serif 4
  mono: IBM Plex Mono
  weights: '400,600'
  italic: true
layout: cover
---

<div class="eyebrow">Montana State University / Faculty Workshop</div>

# Effective AI For Engineering Faculty

<div class="byline">Carson Gross / Gianforte School of Computing / Nov 4 2026</div>

<img class="cover-logo" src="/bobcat.png" alt="MSU Bobcat logo">

<!--
Before this slide: ask for a topic and start the agent. See demos/00_opener.md
-->


---

# About Me

* Carson Gross, Instructor, Gianforte School of Computing
* Creator of [_htmx_](https://htmx.org), co-author of [_Hypermedia Systems_](https://hypermedia.systems)
* I began using AI extensively roughly 18 months ago for programming & class work

::right::

<course-list />

---

# Today's Talk

* I'm going to give you six big ideas around using AI effectively
* I'm going to focus mainly on demos
* I'm recording this and will publish everything, including a transcript, to a website
  * No need to take notes

::right::

## The Big Ideas

1. Learn The Command Line
2. LLMs &nbsp; _Love_ &nbsp; Text
3. Killer Visualizations
4. Think &nbsp; **Big**
5. Automate The Grind
6. Protect Learning

---
layout: idea
n: 1
---

# Learn The Command Line

## Agentic work is local, not in a chatbot

---

# Chat vs Agent

* Most people use AI in a chat window
* Chat sees only what you paste in
* Chat hands back text you copy out

::right::

<chat-vs-agent />

---

# Coding Agents

* A _Coding Agent_ is a local program that can:
* Read and write your files
* Runs commands, edits in place
* Works with you in a loop, like a conversation

::right::

<coding-agent />

---

# The Terminal

* The _terminal_ is a text interface to your computer: you type in commands, 1970s style
* Agents work well in terminals: text in/text out is what LLMs do
* They can run commands as well
* A recurring irony of AI/LLMs: _Old technologies are becoming important again_

::right::

<mac-terminal />

---

# Coding Agents: Not Just For Code

* The name Coding Agent is misleading: an agent can work on _any_ text file (and, increasingly, on non-text files)
* I use them for lectures, quizzes, syllabi, grading scripts, etc
* They can be used effectively for lab reports, LaTeX and MATLAB, etc.
* You will be surprised!

::right::

<any-text-file />

---
layout: idea
n: 2
---

# LLMs &nbsp; _Love_ &nbsp; Text

## If an agent can read it, an agent can help with it

---

# Using Plain Text 

* In order to minimize agentic friction I keep my course materials in plain text formats as much as possible
  * Mainly [_markdown_](https://www.markdownguide.org)
* For slides, I use [_Slidev_](https://sli.dev), a markdown-based slide system
* Non-text formats like Word & PowerPoint are harder for agents to work with
* Again, LLMs driving us back to older technologies!

::right::

<markdown-doc />

---

# Source Control

* Text works well with _source control_: tools like _git_ that save versions of your files
* A _diff_ shows what changed between two versions, like Track Changes in MS Word
* So I can read each change the agent makes, and undo it if it is wrong

::right::

<text-diff />

---

# `AGENTS.md`

* Agents look for a specific Markdown file in the directory (and parent directories) of where you are working: `AGENTS.md`
* You write your rules there once: format, tone, what not to touch
* It can point to other files, so the agent reads the slide rules only when it writes slides

::right::

<agents-file />

---
layout: idea
n: 3
---

# Killer Visualizations

## Build the visualizations you always wanted in class

---

# Interactive Diagrams

* Custom interactive diagrams used to cost too much to build for one lecture
* Now I describe the diagram, and an agent creates it
* Here is a diagram of a binary adder

::right::

<live-figure file="full-adder.html" title="Interactive full adder" />

---

# Gamifying Learning

* Another thing I am doing is _gamifying_ learning for my students
* NAND-to-add is a game to build an 8-bit adder up from NAND gates
* [nand-to-add.cs.montana.edu](https://nand-to-add.cs.montana.edu)

::right::

<img class="shot" src="/shots/nand-to-add.png" alt="The NAND Game">

---
layout: idea
n: 4
---

# Think _Big_

## You probably don't realize what you can do now

---

# MTMC-16

* A 16-bit educational computer, with an emulator, an assembler and tooling
* Registers, memory, a file system and a terminal, all on one screen
* Initially built by hand, reworked with AI to be more like x86
* [mtmc.cs.montana.edu](https://mtmc.cs.montana.edu)

::right::

<img class="shot" src="/shots/mtmc.png" alt="The MTMC-16 emulator">

---

# Scott CPU

* A gate-level emulator of the computer from _But How Do It Know?_
* Entirely vibe coded
  * It was a *long* process getting it just right!
* [scott-cpu.cs.montana.edu](https://scott-cpu.cs.montana.edu)

::right::

<img class="shot" src="/shots/scott-cpu.png" alt="The Scott CPU emulator">

---

# catatui

* The Montana State command line agent, works with the free MSU CatChat models
* Has a `ta` option to flip into teaching mode
* [github.com/msu/catatui](https://github.com/msu/catatui)

::right::

<catatui-screen />

---
layout: idea
n: 5
---

# Automate The Grind

## Let agents deal with the tedium: automate, automate, automate

---

# Grade Transfer

* Final grades live in a CSV from canvas, university grade form takes them one at a time by hand
  * Not on my watch!
* An LLM-generated script turns the grade CSV into JavaScript to fill in the form
* Requires low level web knowledge to use, but I'm happy to share it

::right::

<grade-form />

---

# Course Chores

* Interactively generate quizzes, answer keys and TA rubrics from lecture notes
* Generate podium notes from the deck for me to review before lectures

::right::

<course-pages />

---

# Lecture Reviews

* I record lectures on youtube, then download the transcript
* An agent compares what I said to the slide deck
* It proposes fixes, timing issues, etc for next time
  * Very helpful

::right::

<file-panel name="LECTURE-REVIEWS.md" :lines="['# Lecture Reviews', '', 'A review compares the transcript of a', 'recorded lecture with its deck, and', 'proposes fixes.', '', '* Show me a summary of the analysis', '* Do not change the deck until I tell you', '* Expect transcription errors', '* Do not put everything I say on a slide']" />

---
layout: idea
n: 6
---

# Protect Learning

## AI is a tool, that tool can be used for good or for evil...

---

# Assessment

* I have gone to handwritten quizzes, in person, every three weeks
* One page of handwritten notes
* Assignments are valuable for students who actually do them, but are no longer effective assessment tools
* There's that irony again: butt-in-chair tests... old-timey!

::right::

<quiz-page />

---

# Student Data

* GENERAL LLMs MUST NOT HANDLE FERPA PROTECTED DATA
* When working with a private company LLM (ChatGPT, Claude) assume anything you send is not private
* catatui/CatChat _can_ handle student data, but _be careful_
* I have extensive guards to prevent student data from leaking into LLM sessions

::right::

<data-firewall />

---

# LLM Concerns

* _Prompt injection_: agents act on text they read, files can carry hostile instructions
* _Almost Right Answers_: LLMs generate statistically plausible responses, so what they say always _looks_ right, even if it isn't

::right::

<injection-doc />

---

# LLM Concerns

* _The Sorcerers Apprentice Problem_: Easy to build systems that you don't understand and can't control
* _Social Concerns_: AI companies are run mainly by supervillians 😞

::right::

<injection-doc />

---

# My Essays On AI

* I write about all of this on the [htmx essays page](https://htmx.org/essays/all/)
* If you read only one, read [_The University In The AI Era_](https://htmx.org/essays/universities-and-ai/)

::right::

## Essays

1. [The University In The AI Era](https://htmx.org/essays/universities-and-ai/)
2. [Working With AI: A Concrete Example](https://htmx.org/essays/working-with-ai/)
3. [Code is Cheap(er)](https://htmx.org/essays/code-is-cheap/)

---
layout: default
---

# Summary

* Learn to use command-line agents
* Move course material to plain text (an LLM can help!)
* Learn Markdown
* Build out your `AGENTS.md`
* Build the visualizations you always wanted
* Think big about what you can build
* Let agents automate the grind
* Protect learning with old-timey assessments
* Don't let an LLM near FERPA data

---
layout: end
---

<div class="end-row">
  <div class="end-site">
    <img src="/bobcat.png" alt="MSU Bobcat logo">
    <h1>Effective AI For Engineering Faculty</h1>
  </div>
  <div class="end-link">
    <img class="end-qr" src="/site-qr.png" alt="QR code for https://msu.github.io/msu-ai-workshop/">
    <a href="https://msu.github.io/msu-ai-workshop/">https://msu.github.io/msu-ai-workshop/</a>
  </div>
</div>
