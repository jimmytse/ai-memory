# ai-memory

Dual-branch long-term memory system optimized for free mobile AI.

## Branches

| Branch     | Purpose                          | Format          | Who writes     |
|------------|----------------------------------|-----------------|----------------|
| `main`     | Low-token AI working memory      | Compact JSON    | AI only        |
| `obsidian` | Human-readable + offline input   | Clean Markdown  | Human + AI     |

## Conflict rule
Human edits on `obsidian` are source of truth for human-readable content.  
AI updates on `main` are source of truth for compact working memory.  
When both change the same fact, AI must surface the conflict instead of silently overwriting.

## How to use

**Fresh chat**
- Load `MEMORY.ai.json` + relevant file from `projects/`

**Process offline notes**
- Command: `process inbox` or `check offline notes`

**After important work**
- AI writes short summary to the `obsidian` branch