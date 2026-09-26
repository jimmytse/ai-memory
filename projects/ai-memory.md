# Project: ai-memory

**Status:** Setup  
**Goal:** Low-token dual-branch memory system for free mobile AI + offline Obsidian reading

## Key Decisions
- `main` branch → compact JSON (AI only, lowest tokens)
- `obsidian` branch → clean Markdown (human readable + offline input)
- One compact file per project on AI side
- Inbox processed only by command
- AI writes short summaries to the human side
- Human edits on obsidian = source of truth for human content; AI on main for compact; surface conflicts

## Next Steps
- [ ] Test loading compact memory from a fresh Grok chat
- [ ] Test “process inbox” flow
- [ ] Decide how to archive old inbox notes

## Log
- 2026-09-26: Design finalized, repo renamed to ai-memory
- 2026-09-26: v1 schema + log + conflict rule implemented

## Notes
Created 2026-09-26.