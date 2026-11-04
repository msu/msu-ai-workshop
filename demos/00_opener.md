# Demo: Opener

## Shows

* The room picks a topic, and an agent makes a lecture deck for it
* The expert in the room reviews the result
* One follow-up prompt changes the deck

## Setup

* Rehearse once on the room network, and time it
* The run folder is `lecture/`. Its `AGENTS.md` tells the agent to use `LECTURES.md` and `VOICE.md`
* Open two windows: this deck, and a terminal in `lecture/`
* Set the agent to accept edits, so permission prompts do not stop it
* Default topic: TODO
* Fallback deck: `lecture/fallback.md`, made on the default topic before the talk

## Flow

1. Before any slides, ask: "Give me a lecture you teach this semester"
2. Type the prompt below with that topic
3. While it runs, present the cover, "About Me" and "Today"
4. When it is done, open the deck in a second Slidev server
5. Ask the person who gave the topic: "What did it get wrong?"
6. Give one follow-up prompt from that critique
7. Go to "Learn The Command Line"

## Prompt

```text
Write a Slidev lecture on <TOPIC>.
```

## Open The Result

```bash
npx @slidev/cli deck.md --port 3033
```

## Follow-Up Prompt

```text
<from the critique, for example: cut slide 4, add a worked example>
```

## Fallback

* If the topic is too broad or a joke, use the default topic
* If the network fails or the run takes too long, open `fallback.md`
