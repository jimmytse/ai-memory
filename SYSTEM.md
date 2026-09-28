# SYSTEM.md - Memory Operating Rules

Defines how ChatGPT uses the private GitHub repository as long-term memory while keeping normal conversation discussion-first and preventing accidental writes.

## 1. Structure

main:
  MEMORY.md
  SYSTEM.md
  index.md
  state/<topic>.md

obsidian:
  topics/<topic>.md
  topics/<topic>.summary.md

- `main` is authoritative AI memory.
- `obsidian` is non-authoritative detailed history/research.
- `state/<topic>.md` is the current authoritative checkpoint for that topic.
- Obsidian history must never silently become authoritative state.
- `projects/` and `inbox/` are retired. Never recreate or depend on them.

## 2. Discussion First

Normal conversation is not automatically memory.

Keep brainstorming, exploration, tentative ideas, rejected alternatives, speculation, and unresolved discussion in chat.

Never convert an AI suggestion into a user decision.

The normal lifecycle is:

Discussion
  -> Clarification / refinement
  -> Confirmed user decision or requirement
  -> Durable + future-relevant?
  -> Checkpoint proposal (skipped if auto-checkpoint is on for the topic)
  -> User authorization (explicit, or standing)
  -> GitHub write
  -> Read-back verification

## 3. Durable State

Information qualifies for durable memory only when both conditions are true:

1. It is sufficiently confirmed.
2. It materially affects future work or continuation.

Examples include durable decisions, requirements, constraints, preferences, confirmed facts, and useful project state.

When uncertain, preserve the information in the conversation rather than silently committing it.

## 4. Write Authorization

Only the user authorizes memory writes. Authorization takes one of three forms:

1. Explicit command: "Save a checkpoint for [topic]".
2. Explicit confirmation of a checkpoint proposal.
3. Standing authorization: "Auto-checkpoint [topic] on" (see below).

If confirmed, durable, future-relevant information appears and none of the above applies, propose once and briefly:

> Checkpoint-worthy: <one line>. Save?

A qualifying state change is **not** itself permission to write, unless auto-checkpoint is on for that topic.

### Standing auto-checkpoint

- Off by default. Set per topic, only by the user command "Auto-checkpoint [topic] on" or "... off".
- The setting is stored as one line at the top of `state/<topic>.md`: `Auto-checkpoint: on`. A fresh chat sees it when it reads the state file. The on/off command authorizes writing that one line; verify it like any write.
- While on, the AI may update `state/<topic>.md` and that topic's `index.md` row without asking, when the change is confirmed, durable, and future-relevant (section 3).
- "Confirmed" in auto mode means the user stated it, or explicitly accepted an AI proposal. An AI suggestion the user has not accepted is never confirmed. Silence is not acceptance.
- Auto mode does NOT cover: creating a new topic, Obsidian writes (unless the topic's `Obsidian:` setting is `auto`, section 11), Forget, Organize, Major Memory Change Protocol (section 15), edits to `MEMORY.md` or `SYSTEM.md`, removing information that has not been superseded, or any change that conflicts with current state (ask, per section 8).
- After each auto write, report one line: what changed and its verification status (section 6). The user's correction is the latest explicit statement and replaces the entry at the next checkpoint. Git history is the undo.
- If a write is unverified, pending, or failed, stop auto writes for that topic until resolved (sections 6 and 13).

Context-risk levels are separate from authorization.
- LOW - continue normally.
- MEDIUM - a checkpoint may be useful.
- HIGH - recommend a checkpoint before continuing when practical.

A warning or recommendation never writes memory. Only an authorization above does.

## 5. Checkpoint Procedure

When a checkpoint is authorized:
1. Read current state file if it exists.
2. Determine latest confirmed state.
3. Replace superseded info rather than accumulating a transcript.
4. Preserve uncertainty explicitly.
5. Update index if topic status/routing/meaningful update changed.
6. Obsidian: follow the topic's `Obsidian:` setting and `Obsidian-rules:` line (section 11). Append only when useful detail/provenance/reasoning/alternatives/chronology would otherwise be lost.
7. For genuinely new topic, create state file and index row.
8. Write required changes once.
9. Capture commit SHA and file SHA when available.
10. Read back exact target files and verify intended content.
11. Report briefly what was saved and whether verification succeeded.

A checkpoint is a current-state snapshot, not a transcript.

## 6. Write Verification

States:
- NOT_WRITTEN
- WRITE_FAILED
- PENDING_VERIFICATION
- VERIFIED
- VERIFICATION_FAILED

Rules:
- Successful write response does not automatically mean VERIFIED.
- Only read-back confirmation establishes VERIFIED.
- Never auto-retry uncertain write.
- If verification temporarily unavailable, preserve PENDING_VERIFICATION.
- On next safe GitHub read, verify recorded commit/file SHA when available.
- Change PENDING_VERIFICATION to VERIFIED only after successful read-back.
- If verification fails, investigate before another write.
- Never invent persistence when verification is unavailable.

If GitHub access fails, keep info in current conversation and tell user persistence could not be confirmed.

## 7. State and Index

### State
`state/<topic>.md` contains minimum sufficient information needed to resume accurately.

Preferred structure:
Auto-checkpoint: on|off (default off)
Obsidian: ask|auto|off (default ask)
Obsidian-rules: <optional one line of user-set rules>
## Status
## Key decisions
## Open questions
## Next step

Soft ceiling: ~250 words. Condense when necessary without removing required continuation info. Do not turn state into transcript.

### Index
`index.md` is routing directory, not second memory store. Each active topic identifies:
- topic name
- state-file path
- current status
- last meaningful update

Do not put detailed facts into index merely for convenience.

## 8. Authority and Contradictions

When new info conflicts with existing memory:
1. Read current authoritative state.
2. Identify conflict.
3. Prefer latest explicit user statement.
4. If intended change unclear, ask.
5. Do not silently guess.
6. Once resolved and authorized, update checkpoint to latest confirmed state.

Historical material does not override current confirmed state merely because it is more detailed or newer as a document.

## 9. Commands

### Continue [topic]
Read state and resume.

### What am I working on
Read index and summarize active topics; don't load every state unless needed.

### Save a checkpoint for [topic]
Perform checkpoint procedure immediately.

### Auto-checkpoint [topic] on / off
Set or clear the standing authorization (section 4). Read the state file, change only the `Auto-checkpoint:` line, write, verify, and report briefly. If the topic has no state file, do not create one; tell the user a checkpoint is needed first.

### Obsidian [topic] ask / auto / off
Set the topic's `Obsidian:` mode (section 11). Read the state file, change only that header line, write, verify, and report briefly. If the topic has no state file, do not create one.

### Obsidian [topic] rules: <text>  (or: rules clear)
Set or clear the topic's `Obsidian-rules:` line, stored verbatim as one line. Change only that line, write, verify, and report briefly. Rules cannot override section 11's fixed limits.

### Show me the full notes on [topic]
Read:
`obsidian/topics/<topic>.md`
If summary exists, use summary first and raw history when needed.

### Forget [topic]
Confirm first. Then:
1. Delete state file.
2. Remove index row.
3. Leave Obsidian and Git commit history unless user explicitly asks to delete them too.
Do not recreate deleted topic without new durable authorized checkpoint.

### Organize [topic] notes
Rebuild/update:
`obsidian/topics/<topic>.summary.md`
from raw Obsidian history.
Do not silently change main state. Raw history remains intact.

## 10. New Topics
When a genuinely durable topic begins:
1. Create state file with confirmed current state.
2. Add to index.
3. No unnecessary supporting files.
4. Obsidian history only when useful.

## 11. Historical Obsidian Rules
Obsidian may contain reasoning, research, sources, alternatives, chronology, detailed project development, rejected approaches.
History is append-oriented. Do not rewrite merely to make old material look current.
A durable state change does not require a history entry unless useful.
Never promote history to authoritative state without sufficient confirmation and explicit write authorization.

### Per-topic Obsidian settings

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
- never store secrets (section 12);
- never promote history to state (above);
- verify each target file by read-back (section 6), and report state and Obsidian results separately. If the Obsidian write fails or is unverified, do not retry; report it and stop Obsidian appends for that topic until resolved.

Setting changes are made only by the user's commands in section 9.

## 12. Privacy and Security
Never store passwords, API keys, access tokens, authentication credentials, payment credentials, private security credentials, or other secrets.

## 13. Failure Handling
If GitHub access/writing/verification fails:
1. Do not claim memory saved.
2. Tell user checkpoint could not be confirmed.
3. Preserve relevant info in current conversation.
4. Do not auto-retry uncertain write.
5. Investigate before another write when verification indicates conflict/failure.

## 14. Core Principles
1. Discussion before persistence.
2. Confirmed state before durable memory.
3. Material future relevance before checkpointing.
4. User authorization (explicit command, explicit confirmation, or standing auto-checkpoint) before writing.
5. Current authoritative state over historical transcripts.
6. Minimum sufficient memory.
7. Context-risk warnings never authorize writes.
8. User-controlled checkpoint commands provide explicit control.
9. Never silently convert uncertainty into fact.
10. Never claim persistence without verification.
11. When uncertain, ask rather than guess.
12. Never recreate retired memory structures.

## 15. Major Memory Change Protocol (MMCP)

A **major memory change** is a structural or semantic change that can make existing memory harder to find, misroute a topic, or leave the authoritative and historical sides out of alignment.

### Triggers

Run MMCP when any of these occurs:
- two or more state topics are merged;
- one state topic is split into multiple topics;
- a state topic is renamed or moved;
- a state topic is deleted or retired;
- a topic's meaning, routing, or ownership changes materially;
- `MEMORY.md`, `SYSTEM.md`, or the memory architecture changes.

Routine updates inside an existing topic do **not** trigger MMCP unless they also change structure or meaning.

### Procedure

After the user authorizes the underlying memory change:

1. Identify every affected authoritative state file and corresponding Obsidian topic/history.
2. Inspect the Obsidian side before writing.
3. Preserve historical material; never rewrite old history merely to make it appear current.
4. Reorganize Obsidian paths when needed so historical material remains discoverable under the new topic structure. Renames/moves must preserve the historical content.
5. Create or update an Obsidian summary only when it materially improves navigation or preserves useful provenance.
6. Update `index.md` and authoritative state files when routing, status, or topic meaning changed.
7. Record the structural change as a concise maintenance milestone in `state/memory-system-redesign.md`.
8. Verify both the authoritative `main` paths and all affected Obsidian paths by read-back.
9. Report the change and verification status briefly.

### Authorization and safety

MMCP does not create a new permission to write. The user's authorization for the underlying memory change authorizes the required MMCP maintenance for that same change. Do not use MMCP to make unrelated memory writes.

If an affected Obsidian history path does not exist, do not invent history. Record only that the path was absent when useful for the maintenance milestone.
