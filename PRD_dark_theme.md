# Product Requirements Document: Dark Theme

## Summary

Add an optional dark color theme to the standalone Memory Game in `memory-game.html`. Players can switch between the current light theme and a new dark theme without changing how the game is played or how results are stored.

This document specifies the feature; it does not implement it.

## Background

The game currently uses a light palette defined by CSS custom properties in the page's embedded stylesheet. The page includes the game board, cards, controls, statistics, grid-size buttons, best-scores panel, and a completion dialog. These surfaces should remain readable and visually consistent when dark theme is active.

The application is self-contained and has no backend. Any saved theme choice must therefore be stored locally in the browser.

## Goals

- Let players explicitly switch between light and dark themes.
- Preserve the existing light appearance as the default for players without a saved theme preference.
- Remember a player's selected theme across page reloads in the same browser.
- Keep all game interactions, layouts, game state, and saved scores working as they do today.
- Maintain clear text, controls, focus indicators, and card states in both themes.

## Out of scope

- Automatically following the operating system's theme preference.
- Adding new game modes, score rules, or gameplay behavior.
- Changing the existing layout, card animations, grid sizes, or score-ranking logic.
- Synchronizing preferences or scores between browsers or devices.
- Adding a CSS framework, external library, build step, or backend.

## User stories

1. As a player, I can find a theme control without leaving the game.
2. As a player, I can switch themes while playing and continue the same game.
3. As a returning player, I see the theme I previously selected in this browser.
4. As a keyboard or assistive-technology user, I can identify and operate the theme control and understand its current state.

## Functional requirements

1. Provide a visible theme toggle in the existing page, near the other game controls, with clear text such as “Dark theme” or “Switch to dark theme.”
2. Activating the toggle switches immediately between light and dark themes without reloading the page.
3. The theme applies consistently to the page background, text, statistics panel, grid-size controls, card faces, best-scores panel, win dialog, and interactive states (including hover and keyboard focus).
4. The current light palette remains the initial theme when no valid saved preference exists.
5. Save the player's selected theme in `localStorage` using a theme-specific key. Read and apply a valid saved preference on page load. Do not reuse or modify the `memoryGameScores` key or its data.
6. Expose the toggle's purpose and state to assistive technology using an appropriate accessible name and state (for example, a button with `aria-pressed`). It must be reachable and operable by keyboard.
7. Changing themes must not reset or modify the board, card positions, flipped or matched cards, move count, timer, rating, selected grid size, win-dialog state, or best scores.
8. Theme styling should use the existing CSS custom-property approach where practical so both palettes can be maintained without duplicating page or game markup.

## Visual and accessibility requirements

- Use a cohesive dark palette with distinct page, panel, card-front, and card-back surfaces. Preserve sufficient visual distinction between face-down, revealed, and matched cards.
- Keep text and control labels legible against their backgrounds. Meet WCAG 2.1 AA contrast targets: at least 4.5:1 for normal text and 3:1 for large text and meaningful UI boundaries/indicators.
- Keep visible keyboard focus indicators in both themes; do not rely on color alone to indicate focus or selection.
- Preserve responsive behavior and avoid introducing horizontal overflow at the existing mobile breakpoint.
- Theme changes must not interfere with the card-flip animation or make emoji symbols difficult to see.

## Acceptance criteria

- [ ] A first-time visitor sees the existing light theme.
- [ ] The theme toggle switches between light and dark without a page reload.
- [ ] The selected theme remains active after reloading the page in the same browser.
- [ ] An absent or unrecognized saved preference falls back to light theme.
- [ ] All listed page surfaces and interactive states are styled appropriately in both themes.
- [ ] The toggle is keyboard operable, has an accessible name, and communicates its state.
- [ ] A theme change during a game preserves the current board, timer, moves, rating, and grid selection.
- [ ] Completing games in either theme still saves and displays the existing best-score data.
- [ ] Both themes remain usable at desktop and mobile widths, including when the win dialog is shown.
- [ ] Existing mouse and keyboard gameplay, grid switching, card matching, and Play Again behavior remain unchanged.

## Verification plan

1. Open `memory-game.html` with no saved theme preference and confirm the light theme remains the default.
2. Toggle to dark, inspect the game controls, both card states, best-scores area, and completion dialog, then reload and confirm dark theme persists.
3. Toggle back to light and reload to confirm the choice persists in the other direction.
4. Start a game, change themes mid-game, and verify card positions/states, timer, moves, rating, and selected grid size are unchanged.
5. Complete a game in each theme and confirm score saving, score display, and Play Again still work.
6. Operate the toggle and game using keyboard only; check its accessible state and visible focus in both themes.
7. Check both themes at desktop and narrow/mobile viewport widths for contrast, legibility, and overflow.
8. Confirm the theme preference uses a separate `localStorage` key and existing `memoryGameScores` entries are unchanged.

## Implementation notes

- The game is currently contained in `memory-game.html`; keep the feature self-contained unless implementation uncovers a concrete reason otherwise.
- No dependencies or backend changes are expected.
- Once implementation is complete, the player will manually run the game and review the behavior.
