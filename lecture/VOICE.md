# Voice

How Carson writes lectures. Derived from the CSCI 468 decks, which are hand-written.

`AGENTS.md` gives the structural rules for slides. This file gives the voice. Where the two
conflict, see the last section.

## Person

* Write in first person singular. Do not hide behind the passive or the institutional "we"
  * "I am going to implement the following"
  * "I don't like generating the code for my Syntax Tree"
  * "This is the algorithm I am going to teach you in this class!"
* Address the student directly as "you"
  * "See if you can figure out what it is"
  * "Congrats, you're lexing!"
* Use "you" for work a developer does to the code. Keep "I" for opinions
  * "To add Mac, you must edit every `new WindowsButton()` call"
  * "For two rates I would probably use an `if` statement"
* Use "we" only for work done together in the room
  * "Let's do a read-through of the catscript grammar together"

## Stance

Have an opinion. Label it as an opinion. Teach the thing anyway.

* Never invent an "I prefer" or "I think". Write a first-person opinion only when Carson stated
  it, in a deck or a transcript. Otherwise present the option neutrally
  * not "I prefer passing it in: _dependency injection_"
  * "An alternative is to pass the `Database` into the constructor: _dependency injection_"
* Mark preference as preference, not as fact
  * "Note that this uses a ternary expression here / I'd prefer an if statement"
* Teach material you dislike, and say you dislike it
  * "Yet again I find myself having to teach you something I do not like"
  * "As I said, I am not a fan of this approach for this particular problem / I do understand
    why the author is doing it though and it is a common approach"
* Deflate a technique after showing it, rather than selling it up front
  * "OK, so... what?"
  * "I guess that's kinda good"
  * "And man, that's a lot of classes..."
* Push back on received wisdom, with a reason
  * "Generally, I think that a lot of big brain developers over-complicate things"
  * "This is _not_ how I was taught compilers & is not how most colleges teach parsing"
* Overstate confidence as a joke, and let the joke show it is one
  * "So maybe I'm wrong (I'm not)"
  * "I don't care"

## Anecdote

Career stories carry the argument. Use them where a claim needs authority.

* The Stanford and Guidewire story in `08_recursive_descent.md` runs six slides and exists only
  to prove one point: recursive descent is what real parsers use
* Report reactions as dialogue
  * "Wait, that's it?" / "Yep..." / "That's what a grammar is?" / "Yep..."

## Slide rhythm

* One idea per slide. Two or three short bullets, often one
* Hold the right column fixed across a run of slides. Advance only the left
  * `08_recursive_descent.md` holds one image for eight slides under the title
    "Dealing With Ambiguity"
  * Nine slides in a row hold the same `parseEqualityExpression()` body while the bullets walk
    through it line by line
* Repeat the slide title verbatim across such a run. The repeat is the signal that one thought
  continues
* Change code one line at a time between slides, and point at the changed line in the bullet
  * "What if we changed the second `parseComparisonExpression()` call to `parseEqualityExpression()`?"

## Sentence shape

* Short. Fragment where it reads faster
  * "Next, digits"
  * "Pretty simple!"
  * "Same ol' stuff, just different character classes"
* Open bullets with a connective: OK, Well, Now, Next, Finally, So, Again, Note that
  * "OK, what about longer tokens like, say, comments?"
  * "Note that new line characters _are_ allowed in strings in lox"
* Contractions everywhere. "it's", "don't", "you'd", "that's", "we'll"
* Exclamation points are allowed, about one per few slides

## One fact per bullet

* A bullet is one plain statement. Subject, verb, object. Then stop
  * "`@Entity` tells Hibernate this class maps to a table"
  * "`@Table` tells Hibernate the table name"
  * "`@Id` marks the primary key"
* Two facts are two bullets. Do not glue them with ", and" or ", so"
  * not "`@Entity` tells Hibernate this class maps to a table, and `@Table` says which one"
* No tail. A clause hung on the end to justify or soften the statement adds nothing
  * not "`@Id` marks the primary key, and every entity has to have one"
  * not "All short, so that fits the rule"
* No compression either. A fragment or a comma splice is not a statement
  * not "@ManyToOne holds a Category object, not a category_id"
* Say what the code does. The why gets its own bullet when it matters, and no bullet when it doesn't
* "Outline" means few bullets per slide, not fragments. Fragments are for asides ("Pretty simple!"),
  never for the explanation itself
* No comma kickers in a title or subtitle: "The Java Standard, Configured", "Schema Evolution, Under Test".
  Say the whole thing as one plain phrase

## Questions to the class

Direct questions are a teaching device here, not filler. They are answered.

* Pose a question on one slide, answer it on a later slide
  * "Question: why doesn't he have to match() that final quote?"
  * "Question: Why do we have to consume _all_ alphanumeric tokens before we decide if something
    is a keyword?" then a slide starting "Answer: ..."
* End a lecture on a cliffhanger the student can work on
  * "There's a small problem with this approach / See if you can figure out what it is / Next
    time I'll show you the fix"

Do not write questions with no answer. "What if we could...?" and "But is there a better way?"
are not this.

## Admitting the seams

* Admit a simplification when you later correct it
  * "OK, I lied just a bit"
  * "OK, I kinda lied again, sorry"
  * "OK, OK: I'm soft, let me give you a bit of the string tokenizer too..."
* Point at what a design gets wrong
  * "Note that there is _no way_ to include a quote character / Where's the backslash support?"
* Say when something is optional
  * "Not all of this is strictly necessary for parsing, but makes for better error messages"

## Diction

* Idiom over formal register: "get down to brass tacks", "the big guys", "same ol' stuff",
  "gobsmacked", "I just jammed them on the _ParseElement_ directly"
* Say the thing is easy when it is easy. "Believe it or not, parsing isn't that hard",
  "Pretty easy: you just ignore it!"
* Name people and projects by name. Bob Nystrom, Guidewire, gosu-lang, hyperscript
* Use direct, technical language for what code does. Use the precise term, not a vague stand-in
  * not "Only the factory names a concrete class"
  * "Only the factory instantiates a concrete class"
  * not "It names a problem". Write "It describes a problem"
  * not "a factory is just another hop". Write "a factory adds a layer of indirection"
* Idiom is for asides and opinions. The statement of what the code does stays technical
* Use the identifiers from the code on the slide: types, methods, fields
  * not "The subject keeps a list of observers"
  * "The _subject_ keeps a `List<Observer>`"
* Use the type name for what a method takes or returns, not "one" or "it"
  * not "`attach` adds one"
  * "`attach` adds a new `Observer`"
  * A pronoun is fine when the bullet already names the thing it points to
* Say what a method does step by step, and name the methods it calls
  * not "`notifyObservers` calls each one"
  * "`notifyObservers` iterates over each one, calling `update()`"
  * The "calling ..." clause says how the method works. It is part of the fact, not a tail
* Do not use vague phrasal verbs such as "shows up" for a need in the code. Say "is needed"
  * not "Add the factory when a second implementation shows up"
  * "Add the factory when a second `Logger` implementation is needed"
* Do not give software human verbs such as "notice", "want" or "care"
  * not "the compiler won't notice"
  * "the compiler won't catch the error"
* Write "use", not "reach for": "Use a builder when you have many optional parameters"
* Introduce an example with "e.g.", not "like"
  * "_Creational_ patterns create objects, e.g. `User.Builder`"
* Introduce a thing on the slide, or an earlier slide, before you refer to it
  * not "The shipping code calls each notifier by hand" with no shipping code anywhere

## Diagrams

* SVG text is a label, not a sentence. Keep it short, sharp & technical
* Label a box with an identifier from the code: a type, a method, a field
* Do not add a caption that sums up the diagram. The slide bullets do that
  * not "neither side changes, the adapter sits in between"
  * not "each layer adds its part, then calls the one inside"
* The Diction rules apply: no human verbs, no "you"
  * not "wants a Shape". Write "requires Shape"
  * not "you cannot change it". Write "can't be modified"

## Markup

* Emphasis is underscore italic on one word or one term. Roughly 1000 uses across the 468 decks
  against 3 uses of bold. Do not use bold
* ASCII only. One em-dash exists in 36 decks. `&` for "and" is fine in a title, an aside or a bullet
  * "Placing an order uses three classes: `Inventory`, `Payment` & `Email`"
* `(...)` in a call is fine. It shows the call takes arguments: `checkout.placeOrder(...)`
* Put every code identifier in backticks: `List<Observer>`, `Observer`. A bare `<Observer>` can render
  as an HTML tag and vanish
* Mark a term with italics, not quotes: "The _subject_ keeps a `List<Observer>`"
* Bullets are asterisks. No numbered lists
* No freestanding paragraphs, except a quote slide

## Do not

* Do not use marketing words: seamless, powerful, robust, elegant, leverage
* Do not use false consensus: "everyone agrees", "obviously", "of course"
* Do not use unanswered rhetorical questions
* Do not write "We've seen X, but how does Y work?". Write "Now let's look at how Y works"
* Do not write filler bullets to fill a slide. Cut the slide instead
* Do not give a concept a dramatic framing or a human action. State what happens
  * not "With a framebuffer, a straight line becomes a question: which pixels?" and "Bresenham's algorithm answers it"
  * "To draw a line in a framebuffer, a program must pick the pixels closest to it"

## Conflicts with AGENTS.md

Two rules in `AGENTS.md` do not match the 468 decks. Follow `AGENTS.md` unless told otherwise,
but know that the hand-written source disagrees.

* `AGENTS.md` bans rhetorical questions. The 468 decks use direct questions to the class often,
  and answer them. The ban is on the unanswered, marketing kind. The answered kind is voice
* `AGENTS.md` caps a slide at three bullets. The 468 decks often run four or five short bullets
  with nested sub-bullets. Prefer three. Do not split one thought across two slides to obey it

One more note. The global writing rule asks for Simplified Technical English. That rule fits
documentation and commit messages. It does not fit lectures. Lectures use contractions, idiom,
and the first person.
