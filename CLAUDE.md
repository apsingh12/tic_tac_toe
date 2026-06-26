# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Single-file 5×5 Tic Tac Toe game (`index.html`). No build step, no package manager, no dependencies. Open the file directly in a browser to run it.

## Architecture

Everything lives in `index.html` — styles, markup, and script are all inline.

**Game logic (JavaScript):**
- `WINS` — precomputed array of all 28 winning 4-in-a-row combos on a 5×5 grid
- `board` — flat 25-element array, `null | 'X' | 'O'`
- `getResult(b)` — checks `WINS` against a board state; returns `{ winner, combo }` or `null`
- `place(idx, p)` — mutates `board`, renders the SVG mark, marks the cell `.taken`

**AI (vs AI mode):**
- `pickMove()` — entry point; dispatches to random, `critical()`, or `optimal()`
- `critical()` — scans for an immediate win (O) or must-block (X); returns index or `null`
- `minimax(b, depth, maximizing, α, β)` — alpha-beta minimax; depth 2 for Medium, 4 for Hard
- `evaluate(b)` — heuristic scoring all 28 windows; used at leaf nodes
- `orderedEmpties(b)` — sorts moves by proximity to center (index 12) to improve pruning

**UI flow:**
- Mode toggle (2 Players / vs AI) and difficulty chips reset scores and call `init()`
- `init()` resets board state and clears all cell DOM content
- After each human move, if mode is `'ai'`, `scheduleAI()` fires after a 550ms delay with a "thinking" indicator
- Win triggers `endGame()` → `showWinLine()` + `confetti()`
