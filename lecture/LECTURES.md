# Lectures

Read `VOICE.md` in this folder before you write slide text.

* Overview
    * Lectures are done using slidev, a markdown-based slide tool
    * Lectures live in `internal/lectures/` and do not ship to students. The reader ships in their place
        * Do not put solutions or podium material in a deck. Those go in other `internal/` folders
    * `internal/SYNC.md` holds the image rules (location, format, conversion)
* Frontmatter

```yaml
---
defaults:
  layout: two-cols
mdc: true
fonts:
  mono: Cascadia Mono
  sans: Atkinson Hyperlegible
layout: cover
---
```

* Structure
    * Shoot for between 35 and 45 slides per lecture
    * Slide titles are H1 (`#`). Only the `cover` and `end` slides use H2 (`##`), for the sub-title
    * `two-cols` is the default layout, so a slide does not need a `layout:` line for it
        * `internal/lectures/layouts/two-cols.vue` replaces the built-in layout. Tall content
          scrolls. Wide code clips at the column edge, and hover widens it
    * Concepts go on the left slide, code/diagrams/SVGs/photos go on the right slide, divided by a `::right::`
    * Slides should almost always use bulleted lists (not numbered) and no paragraph content unless there is a quote
    * Three bullets per slide on the left is ideal
        * Go to four if every bullet is very short
    * The title slide should use the `cover` layout and consist of a title that is short and to the point, and then
      a sub-title that is more conversational
    * There should be one summary slide at the end that uses the `default` layout
        * The content of the summary slide should be 8 bullet points or less, most important information
    * The title slide should repeat at the end of the slide show, but using the `end` layout
* Content
    * Use asterisk bullets for lists
    * Use italics for emphasis
    * Always define new terms
    * Titles of slides should be short and to the point, not conversational, and avoid terms like "Best Practices", "Why it works", "The Problem"
        * Keep a title to one line if you can. In `two-cols`, one line holds about 24 characters
        * A few slides can repeat a title. Do not repeat one title across a whole deck
        * For a long run of slides on one concept, you can use `<Concept>: <Slide Description>`, for example "Builders: Too Many Constructors"
            * Use it only for a long run. A plain short title is usually better
            * Do not start the slide description with "The". Prefer a gerund or a verb phrase: "hashCode: Fixing", not "hashCode: The Fix"
    * Avoid "filler" slides like "Pitfalls" or "Common Mistakes"
    * Sometimes a small inline code block can be included in a bulleted list
    * NEVER use filler content (prose or a generic ASCII diagram) on the right
    * Use relevant graphical technical content on the right
        * Sample code, generated SVGs, mermaid diagrams, or relevant images if warranted, roughly in that order
        * For diagrams, prefer a custom SVG in `internal/lectures/public/` to mermaid. Use mermaid only if the diagram it offers matches the concepts exactly
        * Give an SVG a light background panel so it reads on a dark slide
    * Do NOT use freestanding text in most cases: use lists, code blocks & images unless there is a VERY compelling
      reason not to (e.g. quotes)
    * Provide good transitions between major concepts
    * Keep a coherent order of concepts, so the deck builds progressively
        * Finish one concept before you start the next. Do not go back and forth between concepts unless there is a good reason
        * When you rework a deck or add a slide, check the order of the whole deck, not only the new slide
        * If a slide needs a term from a later concept, first ask whether the slide really needs that term
        * Suggest a reorder when you find a problem. Show me the outline before you change the order
    * Before you report a deck as done, check it slide by slide
        * List each new keyword, function and term, including those in demo commands and session files
        * Each one must be explained on that slide, an earlier slide, or an earlier lecture
    * Do not use title slides for concept transitions
    * As much as possible, use ASCII characters
        * You may use basic extended characters for ASCII art or arrows
        * I sometimes put an emoji on a slide. Keep mine. Never add one yourself
    * `style.css` holds only styles that every course can use. Put a one-off style in the deck
        * For one slide, use a `<style>` block on that slide. Slidev scopes it to the slide
        * For a whole deck, use a `<style>` block with `:global(...)` on the cover slide
    * Images use paths relative to the lecture markdown file: `./public/...`
        * Slidev serves `public/` at the root and warns about this form. The images still render, so the warning is safe to ignore
    * Every image has alt text that says what the image shows or teaches, not its file name: `![The CSS box model](./public/css_box_model.svg)`
        * Give a decorative image, such as a logo on a title slide, an empty alt: `alt=""`
        * Do not put `[`, `]`, `{`, `}` or `\` in alt text. Describe the pattern in words. In `![...]`, these can crash the slide, and a backslash sequence is dropped
        * Run `just check-pdfs` after `just gen-pdfs` to find a missing alt
    * Write a component tag in kebab case: `<class-break />` for `components/ClassBreak.vue`.
      The `.vue` file name stays PascalCase
    * `LECTURE-TOOLS.md` holds the names and rules for diagrams, walkthroughs and demos. "Demo" in this file means a code demo
* Tone
    * See `VOICE.md` for person, stance, and phrasing
    * Avoid generic phrasing like "We've seen X, but how does Y work?", prefer "Now let's look at how Y works"
    * Avoid marketing or hype language - present technologies honestly with their tradeoffs
    * Avoid rhetorical questions - "What if we could...?", "But what if...?", "Wouldn't it be nice?", "But is there a
      better way?"
    * Avoid false consensus - avoid "everyone agrees", "obviously", "of course"
    * Maintain a skeptical-but-interested tone - tech is worth understanding, no perfect answer
    * Keep code block comments honest - note costs and tradeoffs
    * Informal, but technically precise. When I edit slides I replace soft terms with the precise technical term
        * "no registers visible to the programmer" -> "no user-facing registers"
        * "segments" -> "segmented memory"
        * "an 8-bit data bus" -> "an 8-bit system data bus"
        * Write the precise term the first time
* Generating New Slides & Editing Existing Slides
    * When generating new slides provide a few bullets per slide with short outline sentence fragments
    * Suggest demo opportunities: demos are almost always better than reading bullet points
    * Open a lecture with a demo only if a good demo exists that students can understand without much context. If not, do not open with a demo
    * Focus on showing rather than telling - favor demos and in-slide visualizations
    * Demo slides should describe _what the demo shows and why it matters_, not how to run it
    * Never write a slide about the demo apparatus: the test class, how it is run, what framework it uses, what switch makes it print. Students see a demo, not the harness. Start the demo on the first slide that uses it, and explain what they are seeing

# Live Editing

Use these when I edit a deck and you work next to me. Do not stop my editing to run them.

* `/cc` comments
    * I write `/cc <request>` in the deck. The event comes when the caret leaves the line
    * Call `mcp__idea__subscribe_cc_todos` with the deck path. Run the command it returns with Monitor
    * For each event, read the current lines, do the request, and remove the comment in the same patch
    * Keep my wording in the lines around the comment. If a patch fails, read the lines again, because I changed them
    * A comment can be half written. If the text stops mid-sentence, use the part that is clear and say what you assumed
    * When you start the watcher again, search the deck for `/cc` to find comments that you missed
* Overflow detection
    * After a batch of changes, run `just check-overflow <deck> <port>` in the background
    * Use a port that is not in use. Do not use my ports, 3030 to 3032
    * Save all files in the IDE first, so the check reads my latest text
    * Look at each screenshot before you report a finding. A right column that scrolls can be what I want
* Error detection
    * Run `just watch-deck <deck>` with Monitor. On each file change, it parses the deck with `parse` from `@slidev/parser`
    * It uses no browser or server. It prints a line only if an error lasts 10 seconds, so half-typed text gives no event
    * If the fix is clear, for example a blank line after `---`, fix it. If not, tell me the line
    * It finds deck parse errors only, not errors in Vue components
* Monitors expire after 30 minutes. If I am still working in the deck, start them again

# Demo Links

* Every code block on a slide that shows demo code starts with a comment that names the demo
    * `// HibernateDemos.lazyLoop()` for one method. Use this form when you can
    * `// HibernateDemos` for a whole class. Put nothing else on that line
    * Use the simple class name. A package prefix is optional
    * `; pow.asm:pow` for a name in a file that is not a class, for example asm, SQL or C--.
      It opens the file at the `pow:` label or the `CREATE ... pow` statement
    * `; pow.asm` for a whole file. Put nothing else on that line
    * The file can have a path prefix, for example `// jdbc/Listing.java`
* The TeachingTools plugin makes these comments links in IntelliJ, in the slides tab and in the markdown editor. Cmd-click opens the demo, so I can go to the demo and back during lecture
* A link comment starts with `//`, `#`, `;` or `--`. Use the comment syntax of the block language. An HTML block cannot link to its demo
* Name a method or label that exists in the code. Before you add a link, find it in the code
* Keep the link line when you edit the code in the block
* Do not put demo output in a demo code block, e.g. a comment with the printed result. Let the demo show it when it runs
