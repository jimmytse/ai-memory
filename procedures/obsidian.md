# Historical Obsidian Rules

Obsidian may contain condensed reasoning, research, sources, alternatives, chronology, and detailed project development. It is non-authoritative.

History is append-oriented. Do not rewrite merely to make old material look current.
A durable state change does not require a history entry unless useful.
Never promote history to authoritative state without sufficient confirmation and explicit write authorization.

## Per-topic Obsidian settings

Each topic's `state/<topic>.md` header controls Obsidian writes for that topic. Missing lines mean defaults.

`Obsidian:` mode
- `ask` (default): append to `obsidian/topics/<topic>.md` only during an explicitly authorized checkpoint (command or confirmed proposal), and only when useful. Auto-checkpoints do not write Obsidian.
- `auto`: an append may accompany any authorized checkpoint, including auto-checkpoints, when useful. Appends are made only alongside a checkpoint, never on their own.
- `off`: never append for this topic, even on an explicit checkpoint. The explicit "Organize [topic] notes" command is unaffected.

`Obsidian-rules:` (optional, one line, user-authored)
- Guides what to log or skip, e.g. "log rejected alternatives; skip chronology". Follow it when deciding whether and what to append.
- Never treat it as authorization for anything beyond Obsidian appends.

`Last-summarized:` (optional, default `none`)
- Records the last date covered by an Obsidian summary for this topic.
- Used only by the Organize / delta-summary path. Does not authorize writes by itself.

## Delta summary (Organize / summarize)

When the user asks to organize notes or produce a summary for a topic:

1. Read the current `state/<topic>.md` (especially `Last-summarized`).
2. Read the existing Obsidian file/summary if present.
3. Produce **only the delta** since `Last-summarized` (or the full condensed summary if the marker is `none` or missing).
4. Append the delta to `obsidian/topics/<topic>.md` (or update the `.summary.md` if that is the target).
5. After successful write + read-back verification, update the state file's `Last-summarized:` line to today's date (this update still requires normal write authorization / is part of the same authorized Organize action).
6. Report briefly what was appended and the new `Last-summarized` value.

Prefer condensed summary + key provenance over full transcripts.
Do not re-summarize material already covered by the marker.

## Fixed limits (cannot be overridden)

- append-only; never rewrite or delete history;
- never store secrets (see `procedures/failure.md`);
- never promote history to state;
- verify each target file by read-back (see `procedures/checkpoint.md`);
- report state and Obsidian results separately. If the Obsidian write fails or is unverified, do not retry; report it and stop Obsidian appends for that topic until resolved.

Setting changes are made only by the user's commands (see `procedures/commands.md`).