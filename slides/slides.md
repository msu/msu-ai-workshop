---
title: AI For Engineering Faculty
info: Montana State University faculty workshop, Nov 4 2026, NAH 137
colorSchema: dark
defaults:
  layout: two-cols
mdc: true
fonts:
  mono: Cascadia Mono
  sans: Atkinson Hyperlegible
layout: cover
---

<div class="eyebrow">Montana State University / Faculty Workshop</div>

# Effective AI

## Using AI as Engineering Faculty

<div class="byline">Carson Gross / Gianforte School of Computing / Nov 4 2026</div>


---

# About Me

* TODO: one line on who I am
* TODO: courses I teach
* TODO: why I started using AI for course work

::right::

<!-- TODO: photo or course list -->

---

# Today

* Six big ideas
* Mostly demos, few bullets
* Everything is on the site, so no need to take notes

::right::

```text
  01  Learn The Command Line
  02  Everything Is Text
  03  Visualizations
  04  Think Big
  05  Automate The Grind
  06  Protect The Learning
```

---
layout: idea
n: 1
---

# Learn The Command Line

## The chat window is the slow way

---

# Chat vs Agent

* Most people use AI in a chat window
* Chat sees only what you paste in
* Chat hands back text you copy out

::right::

```text
  Chat window          Coding agent
  -----------          ------------
  paste a file    ->   reads any file
  copy reply back ->   edits in place
  no memory       ->   project rules
  no commands     ->   runs the build
```

---

# Coding Agents

* A local program that reads your files
* Runs commands, edits in place
* Works in a loop, like a conversation

::right::

```bash
> fix the typo on slide 4

  Read   20_compilers.md
  Edit   20_compilers.md
   -  * a compilier turns source
   +  * a compiler turns source

  Done. One line changed.
```

---

# Coding Agents: Not Just For Code

* TODO: the name is misleading
* TODO: lectures, quizzes, syllabi, grading scripts
* TODO: engineering example outside CS

::right::

```text
  > what does this project do?

  read  AGENTS.md
  read  lectures/ (38 files)
  bash  git log --oneline -5

  "A systems course built around
   two teaching CPUs..."
```

<!--
Demo: demos/01_command_line.md
-->

---

# The Terminal Is Not Scary

* TODO: the few commands you need
* TODO: where to start on Mac and Windows
* TODO: honest note on the learning curve

::right::

```bash
  cd ~/courses/my-course
  claude

  > _
```

---
layout: idea
n: 2
---

# Everything Is Text

## If an agent can read it, an agent can help with it

---

# Plain Text Course Material

* Slides in markdown with _Slidev_
* Readers in _Typst_, PDFs with _pandoc_
* TODO: what this means for Word and PowerPoint users

::right::

```text
  csci-366-template/
    lectures/      slidev decks
    assignments/   one .md per assignment
    demos/         interactive figures
    internal/
      quizzes/
      speaker-notes/
      transcripts/
```

---

# Diffs

* Every agent change shows as a diff
* I read the diff, then I keep it or throw it out
* _git_ is the undo button

::right::

<!-- TODO: screenshot of a diff in IntelliJ -->

---

# Writing Down Your Taste

* Rules live in a markdown file the agent reads every run
* Write your taste once, use it on every task
* Like instructions for an eager TA

::right::

```markdown
# Lectures

* Usually use a two-cols layout
* Three bullets per slide on the left
* Use italics for emphasis
* Avoid "filler" slides like
  "Pitfalls" or "Common Mistakes"
```

---

# Writing Down Your Taste

* TODO: rules come from my own edits
* TODO: when I fix the same thing twice, it becomes a rule
* TODO: voice file example

::right::

```markdown
* Do not start the slide description
  with "The"

  * "hashCode: The Fix"
      -> "hashCode: Fixing"
  * "equals: The Contract"
      -> "equals: Keeping The Contract"
```

<!--
Demo: demos/02_old_deck.md
-->

---
layout: idea
n: 3
---

# Visualizations

## Build the figure you always wanted in class

---

# Interactive Figures

* TODO: what took weeks now takes an afternoon
* TODO: one HTML file, no build, works on any laptop
* TODO: students use them outside class

::right::

```text
  demos/03_binary_computing/
    half-adder.html
    full-adder.html
    full-adder-block.html
    ripple-carry-4.html
    sram-cell.html
```

---

# NAND To Adder

* TODO: build an adder from NAND gates
* TODO: what students learn from it
* [nand-to-add.cs.montana.edu](https://nand-to-add.cs.montana.edu)

::right::

<!-- TODO: screenshot of nand-to-add -->

---

# Live: A Figure For Your Course

* TODO: pick a topic from the room
* TODO: one prompt, one HTML file
* TODO: what I check before I show it to students

::right::

<!-- Demo: demos/03_visualization.md -->

---
layout: idea
n: 4
---

# Think Big

## Projects that were not worth the time before

---

# Scott CPU

* A gate-level emulator of the computer from _But How Do It Know?_
* Every wire on screen is a net in the machine
* [scott-cpu.cs.montana.edu](https://scott-cpu.cs.montana.edu)

::right::

<!-- TODO: screenshot of scott-cpu -->

---

# MTMC-16

* TODO: a teaching computer for the course
* TODO: scope I would not try without AI
* [mtmc.cs.montana.edu](https://mtmc.cs.montana.edu)

::right::

<!-- TODO: screenshot of mtmc -->

---

# Tools For Me

* An IntelliJ plugin to launch Slidev and export PDFs
* Code comments on slides that link to the demo
* TODO: one more

::right::

```java
// HibernateDemos.lazyLoop()
for (Order o : customer.getOrders()) {
    ...
}
```

---

# CatVibes

* A desktop app for MSU students
* Describe an app, CatVibes builds it
* Uses the MSU CatChat models

::right::

<!-- TODO: screenshot of CatVibes -->

---
layout: idea
n: 5
---

# Automate The Grind

## Let the agent write the glue

---

# Grade Transfer

* TODO: the old copy-paste process
* A script turns the grade CSV into JavaScript
* The JavaScript fills in the university grade form

::right::

```just
# Generate grade entry JavaScript from Canvas CSV
# Run by a human only. Agents must not run it:
# its output holds names and grades
gen-final-grade-entries csv_path:
    uv run ... generate_grade_script.py "{{csv_path}}"
```

---

# Course Chores

* Quizzes, answer keys and TA rubrics from lecture notes
* Print-ready PDFs, one question per page
* Podium notes from the deck

::right::

```text
  gen-pdfs
  gen-quizzes
  print-quiz
  gen-notes
  gen-cheatsheets
```

---

# Lecture Reviews

* I record lectures, then get the transcript
* The agent compares what I said to the deck
* TODO: a fix it found

::right::

<!-- TODO: excerpt of a review -->

---
layout: idea
n: 6
---

# Protect The Learning

## AI helps me teach, it must not do the learning for students

---

# Assessment

* Handwritten quizzes, in person
* Written response over multiple choice
* TODO: layered assignments, by hand then with AI

::right::

<!-- TODO: photo of a quiz page -->

---

# Student Data

* Assume anything you send is not private
* All student data lives in one folder
* The agent writes the tool, a human runs it on real data

::right::

```text
  internal/students/<semester>/
    profiles.csv
    submissions/
    grading/

  # never anywhere else
```

---

# Honest Tradeoffs

* TODO: prompt injection
* TODO: wrong answers, stated with confidence
* TODO: the junior developer problem

::right::

<!-- TODO -->

---
layout: default
---

# Summary

* Use a command-line agent, not a chat window
* Keep course material as plain text
* Write your taste down as rules
* Build the visualizations you always wanted
* Think bigger about what is worth building
* Let the agent write the glue, review every diff
* Protect the learning with in-person assessment

---
layout: end
---

<div class="eyebrow">Montana State University / Faculty Workshop</div>

# AI For Engineering Faculty

## How I actually use AI in my courses

<div class="byline">Slides, demos and links: TODO site URL</div>
