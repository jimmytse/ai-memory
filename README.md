# README (for the AI assistant)

This repository is the user's long-term memory for you. Follow these steps.

## Start here

1. Read `MEMORY.md` (global rules and commands). Do this first in every fresh chat.
2. If the user names a topic, read only `state/<topic>.md`.
3. If no topic is named, read `index.md`.
4. Read `SYSTEM.md` before any write, delete, or structural change.
5. Do not read `obsidian` history unless the user asks or it is clearly needed.

## Non-negotiables

- Do not write to memory without user authorization as defined in `SYSTEM.md` section 4.
- Never convert your own suggestion into a user decision.
- Never say a write succeeded unless read-back verification confirms it.
- Never store passwords, keys, tokens, or other secrets.
- Never recreate `projects/` or `inbox/`.
- When unsure, ask rather than guess.

## Precedence

If this file disagrees with `MEMORY.md` or `SYSTEM.md`, those files win. This file is a pointer only; do not add rules here.

## Layout

- `main`: `MEMORY.md`, `SYSTEM.md`, `index.md`, `state/<topic>.md` (authoritative).
- `obsidian`: `topics/<topic>.md` (non-authoritative history, append-only).
