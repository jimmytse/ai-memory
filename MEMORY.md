# MEMORY
AI-only memory. Read this first in every fresh chat.

## HARD RULES (never override)
1. Write to main only with explicit authorization or standing Auto-checkpoint.
2. Never invent decisions, quantities, status, or results.
3. After any write: verify before claiming success. If verification fails → report FAILED and stop. Do not continue as if it succeeded.
4. Brainstorming, tentative ideas, and AI suggestions are never memory.

## Branches
- main: authoritative. MEMORY.md, index.md, state/<t>.md, state/<t>.data.md, procedures/*.md
- obsidian: human history, topics/<t>/. Non-authoritative; never overrides state. Never promote content from it without a new authorized checkpoint.
- projects/ and inbox/ are retired. Never recreate.

## Fresh chat
1. Read this file.
2. Topic named: read only state/<t>.md (its Data file only if the task needs the results). Else: read only index.md.
3. Output one compliance line at the start of the first reply when a topic is active:
   `State: <t> | Auto: on/off | Last-checkpoint: <date or none>`
4. Resume from the state. Don't make the user repeat recorded info.
5. Don't read obsidian unless asked or clearly needed.
Stop as soon as you can answer.

## Precedence
1. User's latest statement in this chat.
2. state/<t>.md.
3. Earlier state.
4. Obsidian.
Detail or recency of a document doesn't override confirmed state.
Conflict or unclear intent: ask, don't guess.

## Write rules
- Write only with authorization: explicit command, confirmed proposal, or standing Auto-checkpoint on for that topic.
- Durable = confirmed and affects future work. Otherwise stay in chat.
- Durable change and no authorization: propose once, "Checkpoint-worthy: <line>. Save?", then wait.
- Smallest necessary change.
- Open questions in state: only what's needed to resume, max 3 lines, must be actionable. Other unresolved points stay in chat.
- Dates: use the platform's date if known, else ask the user once. Never guess.
- Repo is public: never store secrets (passwords, keys, tokens, payment info) or personal/sensitive data.
- Never claim a write succeeded unless verified. Never claim exact token counts without a reliable measure.
- Context-risk warnings never authorize writes.

## Procedure map (load only the one needed)
- checkpoint, save, auto-checkpoint, verify, failure: procedures/write.md
- obsidian log or summary: procedures/obsidian.md
- new topic, forget, merge/split/rename topic, system change: procedures/admin.md

## Commands
Continue [t] | What am I working on | Create new topic [t] | Save a checkpoint for [t] | Auto-checkpoint [t] on/off | Obsidian [t] ask/auto/off | Obsidian [t] rules: <text> or clear | Show full notes on [t] | Forget [t] | Organize [t] notes

## State file format
Header (one line each):
Auto-checkpoint: on|off (default off)
Obsidian: ask|auto|off (default ask)
Obsidian-rules: <optional>
Last-checkpoint: none|YYYY-MM-DD
Last-summarized: none|YYYY-MM-DD
Data: <path> (optional)

Sections: ## Status ## Key decisions ## Open questions ## Next step
Checkpoint, not transcript. Cap about 2 KB. Replace, don't append.
Open questions: max 3 lines, actionable only.
Results the user accepted (a list or table) go in state/<t>.data.md: first line is the column header, then one row per item with source + date. Replace whole file, cap about 8 KB. Working or unaccepted candidates never go there.