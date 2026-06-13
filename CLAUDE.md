# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Single-file browser game: a two-player local tic-tac-toe built with React 18 (loaded via unpkg CDN) and JSX transpiled at runtime by Babel Standalone. No build step, no package manager, no bundler.

## Running

Open `index.html` directly in a browser — no server needed.

## Architecture

Everything lives in `index.html`:

- **CSS** (lines 10–144): dark-themed styles. Player X is purple (`#a78bfa`), Player O is blue (`#60a5fa`). Winning cells get a green highlight (`.winning`).
- **React app** (lines 149–248, `type="text/babel"`): three components and one helper:
  - `calcWinner(squares)` — checks all 8 winning lines; returns `{ winner, line }` or `null`.
  - `Cell` — a single board button; receives `value`, `onClick`, `isWinning`.
  - `App` — owns all state: `squares` (9-element array), `xIsNext` (bool), `score` (`{ X, O }`). Win detection runs after every move; score increments immediately on win. `reset()` clears the board but preserves the score.

## Key constraints

- Node.js v14 is installed — Vite and modern npm tooling are not compatible. Keep the project dependency-free or use CDN links only.
