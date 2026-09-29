# MEMORY
AI-only memory. Read this first in every fresh chat.

## Branches
- main: authoritative. MEMORY.md, index.md, state/<t>.md, state/<t>.data.md, procedures/*.md
- obsidian: human history, topics/<t>/. Non-authoritative; never overrides state.
- projects/ and inbox/ are retired. Never recreate.

## Fresh chat
1. Read this file.
2. Topic named: read only state/<t>.md (its Data file only if the task needs the results). Else: read only index.md.
3. Resume from it. Don't make the user repeat recorded info.
4. Don't read obsidian unless asked or clearly needed.
Stop as soon as you can answer.

## Precedence
1. User's latest statement in this chat. 2. state/<t>.md. 3. Earlier state. 4. Obsidian.
Detail or recency of a document doesn't override confirmed state.
Conflict or unclear intent: ask, don't guess.

## Write rules
- Write only with authorization: explicit command, confirmed proposal, or standing Auto-checkpoint on for that topic.
- Brainstorming, tentative or rejected ideas, and AI suggestions are not memory. Never turn an AI suggestion into a user decision.
- Durable = confirmed and affects future work. Otherwise stay in chat.
- Durable change and no authorization: propose once, "Checkpoint-worthy: <line>. Save?", then wait.
- Smallest necessary change.
- Open questions in state: only what's needed to resume, max 3 lines. Other unresolved points stay in chat.
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
Header (one line each): Auto-checkpoint: on|off (default off) / Obsidian: ask|auto|off (default ask) / Obsidian-rules: <optional> / Last-summarized: none|YYYY-MM-DD / Data: <path> (optional)
Sections: ## Status ## Key decisions ## Open questions ## Next step
Checkpoint, not transcript. Cap about 2 KB. Replace, don't append.
Results the user accepted (a list or table) go in state/<t>.data.md: first line is the column header, then one row per item with source + date. Replace whole file, cap about 8 KB. Working or unaccepted candidates never go there.
