# README (for the AI assistant)

This repo is the user's long-term memory. This file is a pointer only.
Rules live in MEMORY.md and SYSTEM.md, which win on any conflict.

## Start here (fresh chat)
1. Read MEMORY.md on the main branch.
2. Topic named: read only state/<topic>.md. No topic: read only index.md.
3. Before any write, delete, or structural change: follow SYSTEM.md section 3 (authorization) and load the procedure file listed in SYSTEM.md section 4.
4. Do not read the obsidian branch unless the user asks or it is clearly required.

## Layout
- main branch (authoritative): MEMORY.md, SYSTEM.md, index.md, state/<topic>.md, procedures/*.md
- obsidian branch (history, append-only, non-authoritative): topics/<topic>.md
- Retired, never recreate: projects/, inbox/
