# Product Requirements Document: Word Search

## Summary

Provide a self-contained Word Search game that players can open directly in a modern browser. Players choose a word theme and puzzle size, locate every listed word in a letter grid, and receive a completion message with their elapsed time.

## Background

The repository contains standalone browser games built with HTML, CSS, and JavaScript. Word Search should follow that approach: no external libraries, build process, backend, or account is required. The existing Memory Game remains separate and unchanged.

## Goals

- Deliver a playable Word Search game in one HTML file.
- Make puzzles easy to start, understand, and replay.
- Support mouse, touch, and keyboard interaction.
- Keep the board usable at desktop and mobile viewport widths.
- Generate valid puzzles reliably for each available theme and difficulty.

## Out of scope

- Online multiplayer, accounts, leaderboards, or server-side persistence.
- Hints, penalties, or scoring beyond found-word progress and elapsed time.
- Custom word entry or downloading additional word packs.
- Dependencies, a build system, or changes to the Memory Game.

## User stories

1. As a player, I can choose a familiar category and difficulty before playing.
2. As a player, I can identify which words remain and which I have found.
3. As a player, I can select words with a mouse, touch, or keyboard.
4. As a player, I can generate a fresh puzzle without reloading the page.
5. As a mobile player, I can use the puzzle without the page overflowing horizontally.

## Functional requirements

1. Provide Animals, Nature, and Food word themes.
2. Provide Easy (8 × 8), Medium (10 × 10), and Hard (12 × 12) difficulties.
3. Generate a grid containing every selected target word, with random filler letters in all remaining cells.
4. Place words in straight horizontal, vertical, and diagonal directions, in either forward or reverse orientation.
5. List every target word and update the found count and list when a word is discovered.
6. Allow a player to select a word by dragging across its first and last letters or, using the keyboard, selecting the first cell and then the last cell.
7. Accept a selection only when it forms a straight line matching an unfound target word in either orientation. Provide clear feedback for incorrect selections.
8. Highlight found words in the grid and visually mark their list entries.
9. Start an elapsed-time counter on the first cell selection or drag; stop it when all words are found or when a new puzzle starts.
10. Announce progress and completion through an accessible live status message.
11. Start a new puzzle when the player changes theme or difficulty or activates the New Puzzle button.
12. Display a completion message and final elapsed time after all target words are found.

## Accessibility and responsive requirements

- Use native labeled select controls and buttons, with visible keyboard focus.
- Ensure each grid cell is keyboard operable and has an accessible name identifying its row, column, and letter.
- Communicate progress and messages through a polite live region.
- Do not rely on color alone to indicate found words; also mark the corresponding word-list entry as found.
- Support touch selection without browser gestures interfering with a drag.
- Keep the page within the viewport at narrow widths. The letter board may scroll within its own container when needed.
- Maintain readable text, clear cell boundaries, and sufficient contrast for controls, letters, and found-word highlights.

## Acceptance criteria

- [ ] The game opens directly from `word-search.html` without external dependencies.
- [ ] Each theme provides a puzzle at each of the three supported sizes.
- [ ] The target-word count matches the selected difficulty: 8, 10, or 12 words.
- [ ] Every listed word is present in the generated grid in one supported straight direction.
- [ ] Filler letters populate all cells not used by placed words.
- [ ] Mouse/touch drag selection can find a word.
- [ ] Keyboard selection can find words by choosing first and last cells.
- [ ] Invalid or non-straight selections do not mark a word as found and provide feedback.
- [ ] Found words are highlighted, crossed off in the list, and reflected in the progress count.
- [ ] The timer starts on first interaction, resets for a new puzzle, and stops on completion.
- [ ] Completion is announced when all words have been found.
- [ ] Theme and difficulty changes start a fresh puzzle with the expected grid dimensions and word count.
- [ ] At narrow mobile widths, the document does not overflow horizontally; the board can scroll within its own area if needed.
- [ ] Keyboard focus remains visible, controls are labeled, and status updates are accessible.

## Verification plan

1. Open `word-search.html` directly in a modern browser.
2. Generate and complete puzzles for all three themes at Easy, Medium, and Hard.
3. Confirm every word in each generated list is present in the grid and the entire grid is populated.
4. Test selection using mouse drag, touch where available, and keyboard selection.
5. Try an incorrect and a non-straight selection and verify neither is accepted.
6. Confirm word highlights, crossed-off entries, progress count, timer, and completion feedback.
7. Change theme and difficulty and use New Puzzle; confirm the board and word list reset.
8. Check keyboard focus, accessible labels, and status announcements.
9. Check a narrow/mobile viewport for page overflow and usable board scrolling.

## Implementation notes

- The game is implemented in [`word-search.html`](./word-search.html), with embedded CSS and JavaScript.
- The word banks and difficulty configuration are local to the page.
- The game does not use local storage or modify Memory Game scores.
