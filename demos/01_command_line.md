# Demo: Learn The Command Line

## Shows

* The agent finds its own context in an existing course repo
* Chat cannot do this, because it sees only what you paste in

## Setup

* Do not use the real template: `internal/` holds student data
* Make a copy with no `internal/` folder:

```bash
rsync -a --exclude internal --exclude .git ../templates/csci-366-template/ ~/demo-366/
```

* Check that the copy has no `internal/` folder and no student data
* Open a terminal in `~/demo-366`, and start the agent

## Prompt

```text
what does this project do?
```

Follow-up prompt:

```text
which lectures cover the stack, and what do students need before them?
```

## Fallback

* TODO: path to recorded video
