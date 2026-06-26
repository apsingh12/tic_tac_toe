# Tic Tac Toe 5×5

A polished, single-file Tic Tac Toe game played on a **5×5 grid** where you need **4 in a row** to win. No build step, no dependencies — just open `index.html` in a browser.

## Features

- **Two game modes** — play against a friend (2 Players) or challenge the AI (vs AI)
- **Three AI difficulty levels**
  - *Easy* — plays randomly
  - *Medium* — blocks obvious threats but makes occasional mistakes
  - *Hard* — uses minimax with alpha-beta pruning (depth 4) for a serious challenge
- **Persistent scoreboard** tracking wins and draws across rounds
- **Animated marks** — X and O are drawn with SVG stroke animations
- **Win line** — an animated line highlights the winning 4-in-a-row
- **Confetti burst** on victory, color-coded to the winning player
- **Ghost preview** — hover over a cell to see where your mark will land
- **Responsive layout** — works on mobile screens

## How to Play

1. Open `index.html` in any modern browser
2. Choose **2 Players** or **vs AI** using the toggle at the top
3. If playing vs AI, pick a difficulty: Easy, Medium, or Hard
4. Players alternate clicking cells — **X always goes first**
5. Get **4 marks in a row** (horizontally, vertically, or diagonally) to win
6. Click **New Game** to reset the board (scores persist between rounds)

## AI Implementation

The AI uses a **minimax algorithm with alpha-beta pruning**:
- Immediately takes a winning move or blocks the opponent's winning move
- Evaluates board positions using a heuristic that scores all 28 four-cell windows
- Prefers center cells in move ordering to improve pruning efficiency
- Hard mode searches 4 moves deep; Medium mode adds randomness for a softer feel

## Tech Stack

Pure HTML, CSS, and vanilla JavaScript — no frameworks, no build tools, no dependencies.
