# MEMORY
AI-only memory. Read this first in every fresh chat.

## BOOT (read first, refuse if you cannot obey)
If you cannot follow every HARD RULE below **and** the Verify steps in procedures/write.md, refuse any write and say so in one line. Do not partially comply.

## HARD RULES (never override)
1. Write to main only with authorization: an explicit command, a confirmed proposal, or a standing Auto-checkpoint for that topic.
2. Never invent decisions, quantities, status, results, dates, or SHAs.
3. After any write, run Verify (procedures/write.md) before claiming success. Never claim success without a VERIFIED line for every changed file. On FAILED, report it and stop; Auto-checkpoint for that topic is off until the user re-enables it.
4. Brainstorming, tentative ideas, AI suggestions, and silence are never memory and never authorize a write.
5. If a rule is unclear or conflicts with the user’s latest statement, ask once and stop. Do not guess.
6. A state file always keeps the full header and all four sections from State file format, and no other header fields. Check before committing; if it doesn't fit, fix it or refuse the write. Creating a topic requires loading procedures/admin.md first.

## Branches
- main: authoritative. MEMORY.md, index.md, state/<t>.md, state/<t>.data.md, procedures/*.md
- obsidian: human history, topics/<t>/. Non-authoritative; never overrides state. Never promote content from it without a new authorized checkpoint.
- projects/ and inbox/ are retired. Never recreate.

## Fresh chat
1. Read this file.
2. Topic named: read only state/<t>.md (its Data file only if the task needs the results). Else: read only index.md.
3. Output one compliance line at the start of the first reply when a topic is active:
   `State: <t> | Auto: on/off | Last-checkpoint: <date or none>`
4. Resume from the state. Don’t make the user repeat recorded info.
5. Don’t read obsidian unless asked or clearly needed.
6. Stop as soon as you can answer. Do not load extra procedures or files “just in case.”

## Precedence
1. User’s latest statement in this chat.
2. state/<t>.md.
3. Earlier state.
4. Obsidian.
Detail or recency of a document doesn’t override confirmed state.
Conflict or unclear intent: ask, don’t guess.

## Write rules
- Durable = confirmed by the user and affects future work. Otherwise stay in chat.
- Durable change and no authorization: propose once — “Checkpoint-worthy: <one line>. Save?” — then wait.
- Smallest necessary change. Replace, never append.
- Open questions in state: only what is needed to resume, max 3 lines, must be actionable. Other unresolved points stay in chat.
- Dates: use the platform’s date if known, else ask the user once. Never guess.
- Multi-file write: one commit if the tool allows it. If it writes one file per call: create = state, then Data, then index last; delete = index first, then files. Never leave an index row pointing to a missing file. Verify all changed files after the last write.
- Never store secrets or sensitive data in GitHub memory, regardless of repository visibility (passwords, API keys/tokens, authentication credentials, payment/account information, or highly sensitive personal data).
- Context-risk warnings never authorize writes.
- Acceptance of results for the Data file requires an explicit user signal in the current chat (examples: “accept these”, “put these in data”, “save these recipes”, “these are final”). Silence, continued discussion, or lack of objection is never acceptance. Unaccepted candidates stay in chat only.
- Hard size limits (refuse the write if exceeded; count characters before committing):
  - State body after the header lines ≤ 1800 characters.
  - Data file ≤ 7000 characters. Over it: keep current items, move history to an obsidian log.
  Estimate is acceptable only when the tool cannot provide an exact count; prefer exact. Never state exact token or character counts without a reliable measure.

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

Sections: ## Now ## Key decisions ## Open questions ## Next step
Topic lifecycle (active|paused|completed|archived, default active) lives only in the index.md Status column, not in state files.
Checkpoint, not transcript. Replace, don’t append.
Open questions: max 3 lines, actionable only.
Results the user accepted (list, table, or complete items such as recipes) go in state/<t>.data.md. First line: the column header, or a one-line description of the item format. Then one entry per item with source + date. Replace whole file. Working or unaccepted candidates never go there. Exception: a draft the user explicitly asks to save so work can resume (for example, the chat is about to hit its limit). Label the entry [draft], keep one draft at a time, and say in the state Next step that a draft is waiting. Once finished it becomes accepted, or moves to an obsidian log.