---
name: tmux-tui-debug
description: Run and debug terminal UIs inside tmux, capture the screen output, and interact via keypresses to understand behavior. Use when a user asks to debug a TUI via tmux, reproduce TUI flows non-interactively, or capture TUI state for analysis.
---

# Tmux Tui Debug

## Overview

Use tmux to run a TUI in a detached session, send keys to drive it, and capture panes to describe what the UI shows. Adapt the steps and keypresses to the specific debugging goal.

## Workflow

### 1) Confirm the launch command
- Ask for the exact command if unclear (e.g., `cargo run -p app`), plus any required env/config.

### 2) Start the TUI in tmux
- Create a detached session: `tmux new-session -d -s <name> '<command>'`.
- Prefer a short, unique session name.

### 3) Capture the initial screen
- Use `tmux capture-pane -t <name>:0 -p` and describe the visible UI.
- If the UI is empty, wait briefly then capture again.

### 4) Drive interactions to meet the goal
- Send keys with `tmux send-keys -t <name>:0 <keys>`, then capture.
- Pick keypresses based on the goal (filters, detail views, help screen, etc.).
- Iterate: send keys → capture → interpret.

### 5) Clean up
- Exit the TUI (often `q`) and kill the tmux session.

## Output expectations

- Report what the UI shows (headers, tables, filters, hints, counts).
- Note any truncation or visual artifacts due to pane width.
- Keep secrets out of logs and summaries.

## Notes

If the command fails or no UI appears, capture stderr/stdout via tmux and report it before retrying.
When sending cancel/escape input, prefer `tmux send-keys Escape` over `tmux send-keys Esc`, since `Esc` may insert text rather than trigger cancel in some TUIs.
