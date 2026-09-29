# Historical Obsidian Rules

Obsidian may contain reasoning, research, sources, alternatives, chronology, detailed project development, rejected approaches.
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

Fixed limits that no setting or rule can override:
- append-only; never rewrite or delete history;
- never store secrets (see `procedures/failure.md`);
- never promote history to state (above);
- verify each target file by read-back (see `procedures/checkpoint.md`), and report state and Obsidian results separately. If the Obsidian write fails or is unverified, do not retry; report it and stop Obsidian appends for that topic until resolved.

Setting changes are made only by the user's commands (see `procedures/commands.md`).