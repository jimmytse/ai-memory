# ai-memory

Dual-branch long-term memory system optimized for free mobile AI.

## Branches

| Branch     | Purpose                          | Format          | Who writes     |
|------------|----------------------------------|-----------------|----------------|
| `main`     | Low-token AI working memory      | Compact JSON    | AI only        |
| `obsidian` | Human-readable + offline input   | Clean Markdown  | Human + AI     |

## How to use

**Fresh chat**
- Load `MEMORY.ai.json` + relevant file from `projects/`

**Process offline notes**
- Command: `process inbox` or `check offline notes`

**After important work**
- AI writes short summary to the `obsidian` branch