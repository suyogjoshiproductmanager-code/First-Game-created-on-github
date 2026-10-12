# Repository Context

## What this project is

This repository contains a small, standalone Memory (also known as Concentration) card game. The goal is to find all matching pairs by turning over two cards at a time and remembering where symbols are located.

The game runs directly in a web browser. It is implemented in a single HTML file with embedded CSS and JavaScript, and has no external libraries, build step, server, or backend requirement.

## What the game does

- Offers a 4x4 board with 8 pairs or a 6x6 board with 18 pairs.
- Shuffles emoji-symbol cards each time a board is initialized.
- Lets players reveal cards by mouse or keyboard and turns unmatched cards back over.
- Tracks elapsed time, moves, and a star rating based on moves.
- Shows a completion dialog with the final game statistics and a Play Again action.
- Stores up to five best results in the browser's `localStorage`, and displays them on the page.
- Adapts its layout to smaller screens and provides basic keyboard and ARIA support.

Scores are stored in the current browser profile under the `memoryGameScores` key. They are local to that browser and device; there is no account or server-side score sharing.

## Repository contents

- [`memory-game.html`](./memory-game.html) — The complete game: page structure, styles, game logic, controls, and score persistence.
- [`README.md`](./README.md) — Feature list and basic play/development instructions.
- `context.md` — This repository overview.

## How to run it

Open `memory-game.html` in a modern browser. Alternatively, start a local HTTP server from the repository directory:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000/memory-game.html`.

## What the name stands for

The repository is named `memory-game-GHCP`. The current README and application do not explain or expand “GHCP”; it is part of the repository name, and its intended meaning is undocumented. The game itself is presented simply as “Memory Game.”
