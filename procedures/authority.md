# Durable State, State/Index, Authority & Contradictions

## Durable State

Information qualifies for durable memory only when both conditions are true:

1. It is sufficiently confirmed.
2. It materially affects future work or continuation.

Examples include durable decisions, requirements, constraints, preferences, confirmed facts, and useful project state.

When uncertain, preserve the information in the conversation rather than silently committing it.

## State and Index

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

Soft ceiling: \~250 words. Condense when necessary without removing required continuation info. Do not turn state into transcript.

### Index
`index.md` is routing directory, not second memory store. Each active topic identifies:
- topic name
- state-file path
- current status
- last meaningful update

Do not put detailed facts into index merely for convenience.

## Authority and Contradictions

When new info conflicts with existing memory:
1. Read current authoritative state.
2. Identify conflict.
3. Prefer latest explicit user statement.
4. If intended change unclear, ask.
5. Do not silently guess.
6. Once resolved and authorized, update checkpoint to latest confirmed state.

Historical material does not override current confirmed state merely because it is more detailed or newer as a document.