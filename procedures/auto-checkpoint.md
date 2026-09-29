# Standing Auto-Checkpoint

- Off by default. Set per topic, only by the user command "Auto-checkpoint [topic] on" or "... off".
- The setting is stored as one line at the top of `state/<topic>.md`: `Auto-checkpoint: on`. A fresh chat sees it when it reads the state file. The on/off command authorizes writing that one line; verify it like any write.
- While on, the AI may update `state/<topic>.md` and that topic's `index.md` row without asking, when the change is confirmed, durable, and future-relevant (see `procedures/authority.md`).
- "Confirmed" in auto mode means the user stated it, or explicitly accepted an AI proposal. An AI suggestion the user has not accepted is never confirmed. Silence is not acceptance.
- Auto mode does NOT cover: creating a new topic, Obsidian writes (unless the topic's `Obsidian:` setting is `auto` — see `procedures/obsidian.md`), Forget, Organize, Major Memory Change Protocol (see `procedures/mmcp.md`), edits to `MEMORY.md` or `SYSTEM.md`, removing information that has not been superseded, or any change that conflicts with current state (ask, per authority rules).
- After each auto write, report one line: what changed and its verification status (see `procedures/checkpoint.md`). The user's correction is the latest explicit statement and replaces the entry at the next checkpoint. Git history is the undo.
- If a write is unverified, pending, or failed, stop auto writes for that topic until resolved (see `procedures/checkpoint.md` and `procedures/failure.md`).