# Memory Game and Word Search

Two standalone browser games built with HTML, CSS, and JavaScript.

## Memory Game

A responsive and accessible Memory (Concentration) card game.

## Features

- 4x4 and 6x6 grid options
- Smooth card flip animations
- Timer and moves counter
- Star rating system
- Local storage for best scores
- Keyboard controls for accessibility
- Responsive design for all devices
- No external dependencies

## How to Play

1. Open `memory-game.html` in a web browser
2. Click or use keyboard (Tab + Enter/Space) to flip cards
3. Find matching pairs to win
4. Try to complete the game with as few moves as possible
5. Switch between 4x4 and 6x6 grids using the buttons

## Technical Details

- Pure HTML, CSS, and JavaScript implementation in `memory-game.html`
- No external libraries or dependencies
- Fully responsive design using CSS Grid
- Accessible with ARIA attributes and keyboard controls
- Local storage for persistent high scores

## Word Search

Open `word-search.html` in a web browser. Choose an Animals, Nature, or Food theme and an Easy, Medium, or Hard grid. Find the listed words by dragging across their letters or selecting the first and last letters with the keyboard. Words can appear horizontally, vertically, diagonally, and backwards. Choose **New Puzzle** at any time to start over.

The Word Search game is self-contained in one HTML file and does not need external dependencies, a build step, or a server.
See [`PRD_word_search.md`](./PRD_word_search.md) for the product requirements and acceptance criteria.

## Development

1. Clone the repository
2. Open `memory-game.html` or `word-search.html` in a web browser
3. Or serve using a local HTTP server:
   ```bash
   python3 -m http.server 8000
   ```
4. Visit `http://localhost:8000/memory-game.html` or `http://localhost:8000/word-search.html`