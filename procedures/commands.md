# Commands

### Continue [topic]
Read state and resume.

### What am I working on
Read index and summarize active topics; don't load every state unless needed.

### Save a checkpoint for [topic]
Perform checkpoint procedure immediately (see `procedures/checkpoint.md`).

### Auto-checkpoint [topic] on / off
Set or clear the standing authorization (see `procedures/auto-checkpoint.md`). Read the state file, change only the `Auto-checkpoint:` line, write, verify, and report briefly. If the topic has no state file, do not create one; tell the user a checkpoint is needed first.

### Obsidian [topic] ask / auto / off
Set the topic's `Obsidian:` mode (see `procedures/obsidian.md`). Read the state file, change only that header line, write, verify, and report briefly. If the topic has no state file, do not create one.

### Obsidian [topic] rules: <text>  (or: rules clear)
Set or clear the topic's `Obsidian-rules:` line, stored verbatim as one line. Change only that line, write, verify, and report briefly. Rules cannot override the fixed limits in `procedures/obsidian.md`.

### Show me the full notes on [topic]
Read:
`topics/<topic>.md` on the `obsidian` branch
If summary exists, use summary first and raw history when needed.

### Forget [topic]
Confirm first. Then:
1. Delete state file.
2. Remove index row.
3. Leave Obsidian and Git commit history unless user explicitly asks to delete them too.
Do not recreate deleted topic without new durable authorized checkpoint.

### Organize [topic] notes
Produce or update the Obsidian summary for the topic using the delta rules in `procedures/obsidian.md`.
- Use `Last-summarized` from the state file to avoid re-summarizing old material.
- Append (or update the summary file) only the new material.
- After verified write, update `Last-summarized` on the state file to today.
- Do not alter other authoritative state content.
Raw history remains intact.

## New Topics
When a genuinely durable topic begins:
1. Create state file with confirmed current state.
2. Add to index.
3. No unnecessary supporting files.
4. Obsidian history only when useful.