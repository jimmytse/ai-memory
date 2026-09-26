# Project: ai-memory

**Status:** Setup  
**Goal:** Low-token dual-branch memory system for free mobile AI + offline Obsidian reading

## Key Decisions
- `main` branch → compact JSON (AI only, lowest tokens)
- `obsidian` branch → clean Markdown (human readable + offline input)
- One compact file per project on AI side
- Inbox processed only by command
- AI writes short summaries to the human side

## Next Steps
- [ ] Create initial files on both branches
- [ ] Test loading compact memory from a fresh AI chat
- [ ] Test “process inbox” flow
- [ ] Decide how to archive old inbox notes

## Notes
Created 2026-09-26.