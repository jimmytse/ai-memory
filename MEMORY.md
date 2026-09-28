# MEMORY.md - Main Branch

Compact bootstrap for a fresh, token-limited chat. Global rules only; detailed operating procedures live in `SYSTEM.md`.

## Branches

- **main**: authoritative AI memory - `MEMORY.md`, `SYSTEM.md`, `index.md`, `state/<topic>.md`.
- **obsidian**: non-authoritative history/research - `topics/<topic>.md` and optional summaries.
- Current truth comes from the latest sufficiently confirmed information in `main/state/`.
- Obsidian history never silently overrides current state.
- `projects/` and `inbox/` are retired; never recreate them.

## Fresh Chat

1. Read `MEMORY.md`.
2. If the user names a topic, read only `state/<topic>.md`.
3. If no topic is named, read `index.md`.
4. Do not read unrelated state files or Obsidian history unless needed or requested.
5. Resume from recorded state; do not make the user repeat information already recorded.
6. Before any write, delete, or structural change, read **only the relevant section(s)** of `SYSTEM.md` for the command being executed. Do not load the entire file.

## Authority

When information differs, use this order:

1. Latest explicit user statement in the current chat.
2. Latest confirmed `state/<topic>.md`.
3. Earlier confirmed state/history.
4. Obsidian historical notes.

Current-chat information controls the conversation, but does **not** automatically authorize a memory write. If intent is unclear, ask rather than guess.

## State Files

Each topic has one authoritative checkpoint:

`state/<topic>.md`

Preferred structure:

Auto-checkpoint: on|off (default off)
Obsidian: ask|auto|off (default ask)
Obsidian-rules: <optional one line of user-set rules>
## Status
## Key decisions
## Open questions
## Next step

A state file is a checkpoint, not a transcript. Keep only the minimum information needed to resume accurately. Soft ceiling: ~250 words; condense when necessary without losing important state.

## Commands

Before any command that writes or deletes, follow the relevant procedure in `SYSTEM.md`.

- **Continue [topic]** - read its state and resume.
- **What am I working on** - read `index.md` and summarize active topics.
- **Save a checkpoint for [topic]** - perform the checkpoint procedure immediately.
- **Auto-checkpoint [topic] on / off** - set or clear the standing authorization for that topic's state file (see `SYSTEM.md` section 4).
- **Obsidian [topic] ask / auto / off** - set how Obsidian history is written for that topic (see `SYSTEM.md` section 11).
- **Obsidian [topic] rules: <text>** (or **rules clear**) - set or clear the topic's one-line Obsidian rules.
- **Show me the full notes on [topic]** - read the Obsidian history; use its summary first when present.
- **Forget [topic]** - confirm first, then follow `SYSTEM.md`.
- **Organize [topic] notes** - follow `SYSTEM.md`; do not alter authoritative `main` state.

## Memory Rules

- Discussion, brainstorming, tentative ideas, rejected alternatives, speculation, and unresolved points are not memory.
- Never convert an AI suggestion into a user decision.
- Durable memory must be sufficiently confirmed and materially relevant to future work.
- Only the user's explicit authorization permits a memory write.
- Authorization means one of: an explicit checkpoint command, an explicit confirmation of a checkpoint proposal, or a standing auto-checkpoint the user turned on for that topic.
- A qualifying state change does **not** by itself authorize a write unless auto-checkpoint is on for that topic.
- Auto-checkpoint covers only that topic's `state/<topic>.md` and its index row. Obsidian writes follow the topic's `Obsidian:` setting (see `SYSTEM.md` section 11). Everything else still needs explicit authorization.
- Context-risk warnings never authorize writes.
- Make the smallest necessary change.
- Never store passwords, keys, tokens, payment credentials, or other secrets.
- Never claim a memory write succeeded unless read-back verification confirms it.
- Never claim exact token/context measurements without a reliable measurement.
- Keep the system mobile-friendly, low-token, and practical for Free-tier use.
- The user is the sole author of authoritative memory; no approval queue or inbox is required.
